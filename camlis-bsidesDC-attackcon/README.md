CAMLIS-BSIDESdc-ATTACKcon - October 2019

# Brief Overview
These conferences happened around the same time at Washington DC/McLean. My original idea was attending only ATTACKcon but I noticed CAMLIS was getting a lot of hype a few days before so I tried to join it too (got lucky!). Wasn't aware of BSidesDC but I also managed to attend a few talks.

These are my compiled notes and take aways from the talks I attended. I was mainly interested in Threat Hunting operations and what's new for techniques, tooling, analysis ideas, etc. There was a lot of content for 5 days and of course I couldn't attend all of them. Check the following links below for all the topics and talks.

## Quick view:
- CAMLIS (25-26 October) - https://www.camlis.org/2019/talks/
- BsidesDC (25-27 October) - https://bsidesdc2019.busyconf.com/schedule
- ATTACKcon (28 precon, 29-30 October) - https://www.mitre.org/attackcon (videos)

### CAMLIS

Camlis.org **2nd Day** - Conference for Applied Machine Learning and Security
Sadly, only managed to attend the 2nd day. Initially I thought CAMLIS was going to be way more academic with some rocket surgery level algorithms and math. Turns out a lot was about practical implementation, jupyter playbooks and awesome inputs for Threat Hunting. Most references can be found here: https://www.camlis.org/2019/program

- **RAPIDS AI** 
https://github.com/rapidsai/notebooks
A really nice jupyter lab notebook: 
https://github.com/rapidsai/notebooks-contrib/blob/master/conference_notebooks/KDD_2019/cyber/Cybersecurity_KDD.ipynb

- A lot of context about using **PageRank** for clustering of events to fight alert fatigue.
Talk: https://www.camlis.org/2019/tutorials/allen
Jupyter Notebook: https://github.com/rapidsai/notebooks/blob/branch-0.11/cugraph/Pagerank.ipynb

- Really nice talk from **Nicholas Carlini** (https://nicholas.carlini.com/) about Adversarial Robustness. https://www.camlis.org/2019/keynotes/carlini
Biggest take away is to use existing ML learning approaches with critical eyes. A lot of things are still experimental and the ML research community might not "be there yet" for having reliable prediction results. Most algorithms for pattern recognition can't tell precisely the difference between samples(audio, images, etc).
> In my view this is more related to supervised learning as I would give extra trust points for my time series analysis (unsupervised) and the clusters/correlations I get from my datasets :)

- **TweetSeeker** - Research tool for extracting relevant IOC, exploits, injections, etc from Twitter. Initial idea came from processing tweets containing exploitation strings and other observables. According to the research/presentation a single tweet was the initial tip for uncovering APT32 via _SquiblyDoo_ usage. 
https://github.com/jrstarke/TweetSeeker

Alternative implementation (around the same idea). Tweet IOC Hunter: http://tweettioc.com/
 
- **EMBER** - Endgame Malware BEnchmark for Research
https://github.com/endgameinc/ember
 The EMBER dataset is a collection of features from PE files that serve as a benchmark dataset for researchers.
 Labelling malware with **AVClass tool** - https://github.com/malicialab/avclass
 
- **Stringsifter** - Machine Learning done by FireEye quick malware analysis overview using ``strings``. #Stringsifter removes most of the noise from the STDOUT when you run ``strings`` over an executable. Is awesome approach for quick eye-rolling analysis. are not there yet. are not there yet
https://github.com/fireeye/stringsifter/

- **Binee** - Binary Emulation Environment focused on introspection of all IO operations. 
https://github.com/carbonblack/binee
Binee provides an envionment to quickly run analysis allowing OS internal mocking for malware samples. There's a lot of space for additional behavior servicing and custom hooks.

- **Rq_feature_engineering** - To be released feature encoders and scalers built specifically for the data types common to information security. https://github.com/gaeltadh/rq_feature_engineering

### BSides DC

JA3 - SSL TLS Fingerprinting **CISCO JOY** - Now hashes but reversable values.
https://github.com/cisco/joy - package for extracting data features from live network traffic or pcap

no-easy-breach-derby-con-2016 - Mandiant leveraged TLS/SSL to detect APT29 (AKA CozyDuke, Cozy Bear)

https://www.slideshare.net/MatthewDunwoody1/no-easy-breach-derby-con-2016

**Abuse CH Blacklist for SSL**: https://sslbl.abuse.ch/ja3-fingerprints/

**JA3er**, a "VirusTotal" for JA3 - https://ja3er.com/

**TrisulNSM** has a ja3prints - https://www.trisul.org/

**JA3 Synergy Dataset** - This research was mentioned in a slide but it's _not open source "yet"_. The idea behind it is to leverage visibility and correlate HTTP traffic with SSL/TLS traffic based upon protocol metadata and approximate timing. User agents correlations with similar kind related to JA3.


### ATTACKcon

- **TRAM** - Threat Report Automation Mapping - Easily map techniques from reports. Available soon follow @sarah_yoder https://twitter.com/sarah__yoder

- **Creating your Own Threat Library** - Lessons learned by Valentina Palacin (@33root) and Ruth Barbacil(@fierytermite) while creating a knowledge book based on CTI Research Teams and OSINT - They proposed a custom method to prioritize intel feeds and how to correlate attribution observables by rating *Type*, *Region Visibility*, *Reputation*, *Availability of IOCs*.

- **Climbing the Att&ck Ladder** - Overwatch Threat Hunting team from CrowdStrike. Karl Scheueurman and Piotr Wojtyla proposing Enhacements for Threat Hunting process. Overview between ATT&CK Hard and Easy way and some Interesting TTPs spotted in the wild. Hard way: Maping everything manually and tracking over time. 
Some TTPs in the wild:
  - **Collection, Clipboard Data (T1115)**
    - GoldStamp implant can access the victim's clipboard
    - Replacing cryptocurrency wallet addresses
  - **Persistence, Browser Extensions (T1176)**
    - Malicious Chrome Extensions
    - Compromised Gmail account used to "advertise" the extension in Chrome Web Browser
  - **Impact, Runtime Data Manipulation (T1494)**
    - Backdoored versions of Linux administration tools
    - Config file had strings to execute from output of commands
    - ``` rm -f ps/*.o```
  - **Credential Access, Input Capture (T1056)**
    - SSH daemon modified
    - auth_password funciont logs login password to adversary designed file
  - **Defense evasion | Execution, CMSTP (T1191)**
    - Batch file launched
    - Ultimately led to writing 2612.inf
    
More at: https://www.crowdstrike.com/resources/reports/observations-from-the-front-lines-of-threat-hunting/

- **Misinformation Threat Sharing** - Sara-Jayne Terp. https://github.com/misinfosecproject/amitt_framework

  - Information space full of pollution
  - Tracking social media
  - Communities Misinformation
  - Narrative tracking
  - Artifacts > Narratives > Incidents > Campaigns
  - Build a big stage-based models

https://misinfosecproject.github.io/tools.html

- **TU Delft - Exploring Malware History** - Kris Oosthoek(@f00th0ld) - https://krisk.io/post/attack/
Analysis of techniques observed during execution of a large sample of malware. Direct link to paper:  https://krisk.io/post/sok-attack-securecomm19.pdf

- **Prioritizing Data Sources for Minimum Viable Detection** - Keith McCammon (@kwm)- Red Canary
A lot of work on Detection engineering (Data, Analytics, Detection). Be critical for knowing which data source you need. Reasoning: "We can't detect what we can't see". 
Guide concepts: Maximize Coverage, Minimize Complexity and Optimize for Answers. 

https://github.com/keithmccammon/python-attack-utils - Tool for manipulating MITRE data sources and techniques for Visibility and Protection.
``` ./attack.py --dump-metadata - Then go nuts with Excel```

Top 10 Data sources by Prevalence:
  - Process Monitoring
  - File Monitoring
  - Process command-line parameters
  - API Monitoring
  - Process use of Network
  - Packet Capture
  - Windows Registry
  - Authentication Logs
  - Netflow/Enclave netflow
  - Windows event logs

https://resources.redcanary.com/hubfs/ThreatDetectionReport-2019.pdf

- **From Susceptible to ATT&CK - A Threat Hunting Story** - Chris Thayer from Mastercard explaining about a Threat Hunting Loop process. 
> My comment: As a quick remark I'm also using feedback loop processes to describe Threat Hunting effort. For me both Threat Hunting Loop and OODA Loops are variations of a known topic from visualization theory for "Overview first, zoom and filter, and then details-ondemand". 
References: "Information Seeking Mantra"[1] and "Feedback loop process"[2]
[1]B. Shneiderman, "The Eye Have It: A Task by Data Type Taxonomy for Information Visualizations", 1996. [2]Visual analytics: Scope and challenges, Keim, 2008

- **MITRE ATT&CK Dat perspective** - Olaf Hartong (@olafhartong)- Presented a toolkit for processing data sources and techniques.
  - Data source weights workbook - With a view of techniques, data source and weights
  - Rating workbook - Provides a rating related to quality dimensions of Completeness, Timeliness, Availability and Score.
  - Technique application workbook - Gives a view of Technique, Data Source and a score from the Alerting, Hunting and Forensics perspective.
  - Graph modeled assessment ilustrates paths and attacked could take based on the relationship of you data sources and you coverage

- **Ready to ATT&CK? Mordor, OSSEM, HuntersForge, etc** - Rodriguez² (@Cyb3rPandaH and @Cyb3rWard0g) -- Too much content! Can't possibly right everything here. (https://youtu.be/L3KxKAGSJp4?t=7818)

  - Creating Hunters-Forge community. @HuntersForge: documentation and standardization of security event logs
https://github.com/hunters-forge/ATTACK-Python-Client

  - OSSEM - https://github.com/hunters-forge/OSSEM - Documentation and standardization of security event logs.

- Lighting Talk - **Tracking and Measuring your Coverage with ATT&CK JIRA** - Mauricio Velazco(@mvelazco) - Using Jira to track you coverage https://github.com/mvelazc0/attack2jira



