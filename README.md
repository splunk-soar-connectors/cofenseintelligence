[comment]: # "Auto-generated SOAR connector documentation"
# Cofense Intelligence

Publisher: Splunk  
Connector Version: 2\.0\.5  
Product Vendor: Cofense  
Product Name: Cofense Intelligence  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 5\.1\.0  

This App integrates with Cofense Intelligence to provide various hunting and reporting actions in addition to threat ingestion

### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a Cofense Intelligence asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**username** |  required  | string | Username
**password** |  required  | password | Password
**poll\_now\_ingestion\_span** |  optional  | numeric | Poll last n days for 'Poll Now'
**first\_scheduled\_ingestion\_span** |  optional  | numeric | Poll last n days for first scheduled polling

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity  
[hunt url](#action-hunt-url) - Look for information about a URL  
[hunt file](#action-hunt-file) - Look for information about a file  
[hunt ip](#action-hunt-ip) - Look for information about an IP  
[hunt domain](#action-hunt-domain) - Look for information about a domain  
[get report](#action-get-report) - Get threat details  
[on poll](#action-on-poll) - Action to ingest threats  

## action: 'test connectivity'
Validate the asset configuration for connectivity

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'hunt url'
Look for information about a URL

Type: **investigate**  
Read only: **True**

The action executes search API, that returns information about every matching report\. The output data is restricted to include only report information and URL queried\. <br>If <b>max\_threat\_count</b> parameter is not specified, the action will use 100\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**url** |  required  | URL to hunt | string |  `url` 
**max\_threat\_count** |  optional  | Maximum threats to fetch | numeric | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.max\_threat\_count | numeric | 
action\_result\.parameter\.url | string |  `url` 
action\_result\.data\.\*\.data\.threats\.\*\.apiReportURL | string |  `url` 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.blockType | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.confidence | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data\_1 | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data\_1\.domain | string |  `domain` 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data\_1\.host | string |  `host name` 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data\_1\.path | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data\_1\.protocol | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data\_1\.url | string |  `url` 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.impact | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.infrastructureTypeSubclass\.description | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.malwareFamily\.description | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.malwareFamily\.familyName | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.role | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.roleDescription | string | 
action\_result\.data\.\*\.data\.threats\.\*\.campaignBrandSet\.\*\.brand\.id | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.campaignBrandSet\.\*\.brand\.text | string | 
action\_result\.data\.\*\.data\.threats\.\*\.campaignBrandSet\.\*\.totalCount | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.executiveSummary | string | 
action\_result\.data\.\*\.data\.threats\.\*\.firstPublished | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.hasReport | boolean | 
action\_result\.data\.\*\.data\.threats\.\*\.id | numeric |  `cofense intelligence threat id` 
action\_result\.data\.\*\.data\.threats\.\*\.label | string | 
action\_result\.data\.\*\.data\.threats\.\*\.lastPublished | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.malwareFamilySet\.\*\.description | string | 
action\_result\.data\.\*\.data\.threats\.\*\.malwareFamilySet\.\*\.familyName | string | 
action\_result\.data\.\*\.data\.threats\.\*\.reportURL | string |  `url` 
action\_result\.data\.\*\.data\.threats\.\*\.threatDetailURL | string |  `url` 
action\_result\.data\.\*\.data\.threats\.\*\.threatType | string | 
action\_result\.summary\.total\_threats | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'hunt file'
Look for information about a file

Type: **investigate**  
Read only: **True**

The action executes search API, that returns information about every matching report\. The output data is restricted to include only report information and file queried\. <br>If <b>max\_threat\_count</b> parameter is not specified, the action will use 100\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**hash** |  required  | File hash to hunt \(MD5\) | string |  `hash`  `md5` 
**max\_threat\_count** |  optional  | Maximum threats to fetch | numeric | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.hash | string |  `hash`  `md5` 
action\_result\.parameter\.max\_threat\_count | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.apiReportURL | string |  `url` 
action\_result\.data\.\*\.data\.threats\.\*\.campaignBrandSet\.\*\.brand\.id | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.campaignBrandSet\.\*\.brand\.text | string | 
action\_result\.data\.\*\.data\.threats\.\*\.campaignBrandSet\.\*\.totalCount | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.executableSet\.\*\.dateEntered | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.executableSet\.\*\.executableSubtype\.description | string | 
action\_result\.data\.\*\.data\.threats\.\*\.executableSet\.\*\.fileName | string |  `file name` 
action\_result\.data\.\*\.data\.threats\.\*\.executableSet\.\*\.fileNameExtension | string | 
action\_result\.data\.\*\.data\.threats\.\*\.executableSet\.\*\.malwareFamily\.description | string | 
action\_result\.data\.\*\.data\.threats\.\*\.executableSet\.\*\.malwareFamily\.familyName | string | 
action\_result\.data\.\*\.data\.threats\.\*\.executableSet\.\*\.md5Hex | string |  `md5` 
action\_result\.data\.\*\.data\.threats\.\*\.executableSet\.\*\.severityLevel | string | 
action\_result\.data\.\*\.data\.threats\.\*\.executableSet\.\*\.sha1Hex | string |  `sha1` 
action\_result\.data\.\*\.data\.threats\.\*\.executableSet\.\*\.sha224Hex | string |  `sha224` 
action\_result\.data\.\*\.data\.threats\.\*\.executableSet\.\*\.sha256Hex | string |  `sha256` 
action\_result\.data\.\*\.data\.threats\.\*\.executableSet\.\*\.sha384Hex | string |  `sha384` 
action\_result\.data\.\*\.data\.threats\.\*\.executableSet\.\*\.sha512Hex | string |  `sha512` 
action\_result\.data\.\*\.data\.threats\.\*\.executableSet\.\*\.ssdeep | string | 
action\_result\.data\.\*\.data\.threats\.\*\.executableSet\.\*\.type | string | 
action\_result\.data\.\*\.data\.threats\.\*\.executableSet\.\*\.vendorDetections\.\*\.detected | boolean | 
action\_result\.data\.\*\.data\.threats\.\*\.executableSet\.\*\.vendorDetections\.\*\.threatVendorName | string | 
action\_result\.data\.\*\.data\.threats\.\*\.executiveSummary | string | 
action\_result\.data\.\*\.data\.threats\.\*\.firstPublished | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.hasReport | boolean | 
action\_result\.data\.\*\.data\.threats\.\*\.id | numeric |  `cofense intelligence threat id` 
action\_result\.data\.\*\.data\.threats\.\*\.label | string | 
action\_result\.data\.\*\.data\.threats\.\*\.lastPublished | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.malwareFamilySet\.\*\.description | string | 
action\_result\.data\.\*\.data\.threats\.\*\.malwareFamilySet\.\*\.familyName | string | 
action\_result\.data\.\*\.data\.threats\.\*\.reportURL | string |  `url` 
action\_result\.data\.\*\.data\.threats\.\*\.threatDetailURL | string |  `url` 
action\_result\.data\.\*\.data\.threats\.\*\.threatType | string | 
action\_result\.summary\.total\_threats | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'hunt ip'
Look for information about an IP

Type: **investigate**  
Read only: **True**

The action executes search API, that returns information about every matching report\. The output data is restricted to include only report information and IP queried\. <br>If <b>max\_threat\_count</b> parameter is not specified, the action will use 100\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**ip** |  required  | IP to hunt | string |  `ip` 
**max\_threat\_count** |  optional  | Maximum threats to fetch | numeric | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.ip | string |  `ip` 
action\_result\.parameter\.max\_threat\_count | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.apiReportURL | string |  `url` 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.blockType | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.confidence | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data\_1 | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data\_1\.domain | string |  `domain` 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data\_1\.host | string |  `host name` 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data\_1\.path | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data\_1\.protocol | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data\_1\.url | string |  `url` 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.impact | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.infrastructureTypeSubclass\.description | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.ipDetail\.asn | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.ipDetail\.asnOrganization | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.ipDetail\.continentCode | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.ipDetail\.continentName | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.ipDetail\.countryIsoCode | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.ipDetail\.countryName | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.ipDetail\.ip | string |  `ip` 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.ipDetail\.isp | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.ipDetail\.latitude | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.ipDetail\.longitude | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.ipDetail\.lookupOn | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.ipDetail\.metroCode | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.ipDetail\.organization | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.ipDetail\.postalCode | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.ipDetail\.subdivisionIsoCode | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.ipDetail\.subdivisionName | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.ipDetail\.timeZone | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.ipDetail\.userType | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.malwareFamily\.description | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.malwareFamily\.familyName | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.role | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.roleDescription | string | 
action\_result\.data\.\*\.data\.threats\.\*\.campaignBrandSet\.\*\.brand\.id | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.campaignBrandSet\.\*\.brand\.text | string | 
action\_result\.data\.\*\.data\.threats\.\*\.campaignBrandSet\.\*\.totalCount | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.executiveSummary | string | 
action\_result\.data\.\*\.data\.threats\.\*\.firstPublished | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.hasReport | boolean | 
action\_result\.data\.\*\.data\.threats\.\*\.id | numeric |  `cofense intelligence threat id` 
action\_result\.data\.\*\.data\.threats\.\*\.label | string | 
action\_result\.data\.\*\.data\.threats\.\*\.lastPublished | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.malwareFamilySet\.\*\.description | string | 
action\_result\.data\.\*\.data\.threats\.\*\.malwareFamilySet\.\*\.familyName | string | 
action\_result\.data\.\*\.data\.threats\.\*\.reportURL | string |  `url` 
action\_result\.data\.\*\.data\.threats\.\*\.threatDetailURL | string |  `url` 
action\_result\.data\.\*\.data\.threats\.\*\.threatType | string | 
action\_result\.summary\.total\_threats | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'hunt domain'
Look for information about a domain

Type: **investigate**  
Read only: **True**

The action executes search API, that returns information about every matching report\. The output data is restricted to include only report information and domain queried\. <br>If <b>max\_threat\_count</b> parameter is not specified, the action will use 100\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**domain** |  required  | Domain to hunt | string |  `url`  `domain` 
**max\_threat\_count** |  optional  | Maximum threats to fetch | numeric | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.domain | string |  `url`  `domain` 
action\_result\.parameter\.max\_threat\_count | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.apiReportURL | string |  `url` 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.blockType | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data\_1 | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data\_1\.domain | string |  `domain` 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data\_1\.host | string |  `host name` 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data\_1\.path | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data\_1\.protocol | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.data\_1\.url | string |  `url` 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.impact | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.infrastructureTypeSubclass\.description | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.malwareFamily\.description | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.malwareFamily\.familyName | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.role | string | 
action\_result\.data\.\*\.data\.threats\.\*\.blockSet\.\*\.roleDescription | string | 
action\_result\.data\.\*\.data\.threats\.\*\.campaignBrandSet\.\*\.brand\.id | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.campaignBrandSet\.\*\.brand\.text | string | 
action\_result\.data\.\*\.data\.threats\.\*\.campaignBrandSet\.\*\.totalCount | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.executiveSummary | string | 
action\_result\.data\.\*\.data\.threats\.\*\.firstPublished | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.hasReport | boolean | 
action\_result\.data\.\*\.data\.threats\.\*\.id | numeric |  `cofense intelligence threat id` 
action\_result\.data\.\*\.data\.threats\.\*\.label | string | 
action\_result\.data\.\*\.data\.threats\.\*\.lastPublished | numeric | 
action\_result\.data\.\*\.data\.threats\.\*\.malwareFamilySet\.\*\.description | string | 
action\_result\.data\.\*\.data\.threats\.\*\.malwareFamilySet\.\*\.familyName | string | 
action\_result\.data\.\*\.data\.threats\.\*\.reportURL | string |  `url` 
action\_result\.data\.\*\.data\.threats\.\*\.threatDetailURL | string |  `url` 
action\_result\.data\.\*\.data\.threats\.\*\.threatType | string | 
action\_result\.summary\.total\_threats | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get report'
Get threat details

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**threat\_id** |  required  | Threat ID | numeric |  `cofense intelligence threat id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.threat\_id | string |  `cofense intelligence threat id` 
action\_result\.data\.\*\.data\.apiReportURL | string |  `url` 
action\_result\.data\.\*\.data\.blockSet\.\*\.blockType | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.confidence | numeric | 
action\_result\.data\.\*\.data\.blockSet\.\*\.data | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.data\_1 | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.data\_1\.domain | string |  `domain` 
action\_result\.data\.\*\.data\.blockSet\.\*\.data\_1\.host | string |  `host name` 
action\_result\.data\.\*\.data\.blockSet\.\*\.data\_1\.path | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.data\_1\.protocol | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.data\_1\.url | string |  `url` 
action\_result\.data\.\*\.data\.blockSet\.\*\.impact | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.infrastructureTypeSubclass\.description | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.ipDetail\.asn | numeric | 
action\_result\.data\.\*\.data\.blockSet\.\*\.ipDetail\.asnOrganization | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.ipDetail\.continentCode | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.ipDetail\.continentName | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.ipDetail\.countryIsoCode | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.ipDetail\.countryName | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.ipDetail\.ip | string |  `ip` 
action\_result\.data\.\*\.data\.blockSet\.\*\.ipDetail\.isp | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.ipDetail\.latitude | numeric | 
action\_result\.data\.\*\.data\.blockSet\.\*\.ipDetail\.longitude | numeric | 
action\_result\.data\.\*\.data\.blockSet\.\*\.ipDetail\.lookupOn | numeric | 
action\_result\.data\.\*\.data\.blockSet\.\*\.ipDetail\.metroCode | numeric | 
action\_result\.data\.\*\.data\.blockSet\.\*\.ipDetail\.organization | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.ipDetail\.postalCode | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.ipDetail\.subdivisionIsoCode | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.ipDetail\.subdivisionName | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.ipDetail\.timeZone | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.ipDetail\.userType | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.malwareFamily\.description | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.malwareFamily\.familyName | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.role | string | 
action\_result\.data\.\*\.data\.blockSet\.\*\.roleDescription | string | 
action\_result\.data\.\*\.data\.campaignBrandSet\.\*\.brand\.id | numeric | 
action\_result\.data\.\*\.data\.campaignBrandSet\.\*\.brand\.text | string | 
action\_result\.data\.\*\.data\.campaignBrandSet\.\*\.totalCount | numeric | 
action\_result\.data\.\*\.data\.campaignLanguageSet\.\*\.languageDefinition\.cultureCode | string | 
action\_result\.data\.\*\.data\.campaignLanguageSet\.\*\.languageDefinition\.isoCode | string | 
action\_result\.data\.\*\.data\.campaignLanguageSet\.\*\.languageDefinition\.name | string | 
action\_result\.data\.\*\.data\.domainSet\.\*\.domain | string |  `domain` 
action\_result\.data\.\*\.data\.domainSet\.\*\.totalCount | numeric | 
action\_result\.data\.\*\.data\.executableSet\.\*\.dateEntered | numeric | 
action\_result\.data\.\*\.data\.executableSet\.\*\.executableSubtype\.description | string | 
action\_result\.data\.\*\.data\.executableSet\.\*\.fileName | string |  `file name` 
action\_result\.data\.\*\.data\.executableSet\.\*\.fileNameExtension | string | 
action\_result\.data\.\*\.data\.executableSet\.\*\.malwareFamily\.description | string | 
action\_result\.data\.\*\.data\.executableSet\.\*\.malwareFamily\.familyName | string | 
action\_result\.data\.\*\.data\.executableSet\.\*\.md5Hex | string |  `md5` 
action\_result\.data\.\*\.data\.executableSet\.\*\.severityLevel | string | 
action\_result\.data\.\*\.data\.executableSet\.\*\.sha1Hex | string |  `sha1` 
action\_result\.data\.\*\.data\.executableSet\.\*\.sha224Hex | string |  `sha224` 
action\_result\.data\.\*\.data\.executableSet\.\*\.sha256Hex | string |  `sha256` 
action\_result\.data\.\*\.data\.executableSet\.\*\.sha384Hex | string |  `sha384` 
action\_result\.data\.\*\.data\.executableSet\.\*\.sha512Hex | string |  `sha512` 
action\_result\.data\.\*\.data\.executableSet\.\*\.ssdeep | string | 
action\_result\.data\.\*\.data\.executableSet\.\*\.type | string | 
action\_result\.data\.\*\.data\.executableSet\.\*\.vendorDetections\.\*\.detected | boolean | 
action\_result\.data\.\*\.data\.executableSet\.\*\.vendorDetections\.\*\.threatVendorName | string | 
action\_result\.data\.\*\.data\.executiveSummary | string | 
action\_result\.data\.\*\.data\.extractedStringSet\.\*\.data | string | 
action\_result\.data\.\*\.data\.feeds\.\*\.displayName | string | 
action\_result\.data\.\*\.data\.feeds\.\*\.id | numeric | 
action\_result\.data\.\*\.data\.feeds\.\*\.permissions\.OWNER | boolean | 
action\_result\.data\.\*\.data\.feeds\.\*\.permissions\.READ | boolean | 
action\_result\.data\.\*\.data\.feeds\.\*\.permissions\.WRITE | boolean | 
action\_result\.data\.\*\.data\.firstPublished | numeric | 
action\_result\.data\.\*\.data\.hasReport | boolean | 
action\_result\.data\.\*\.data\.id | numeric |  `cofense intelligence threat id` 
action\_result\.data\.\*\.data\.label | string | 
action\_result\.data\.\*\.data\.lastPublished | numeric | 
action\_result\.data\.\*\.data\.malwareFamilySet\.\*\.description | string | 
action\_result\.data\.\*\.data\.malwareFamilySet\.\*\.familyName | string | 
action\_result\.data\.\*\.data\.reportURL | string |  `url` 
action\_result\.data\.\*\.data\.senderEmailSet\.\*\.senderEmail | string |  `email` 
action\_result\.data\.\*\.data\.senderEmailSet\.\*\.totalCount | numeric | 
action\_result\.data\.\*\.data\.senderIpSet\.\*\.ip | string |  `ip` 
action\_result\.data\.\*\.data\.senderIpSet\.\*\.totalCount | numeric | 
action\_result\.data\.\*\.data\.senderNameSet\.\*\.name | string | 
action\_result\.data\.\*\.data\.senderNameSet\.\*\.totalCount | numeric | 
action\_result\.data\.\*\.data\.spamUrlSet\.\*\.totalCount | numeric | 
action\_result\.data\.\*\.data\.spamUrlSet\.\*\.url\_1\.domain | string |  `domain` 
action\_result\.data\.\*\.data\.spamUrlSet\.\*\.url\_1\.host | string |  `host name` 
action\_result\.data\.\*\.data\.spamUrlSet\.\*\.url\_1\.path | string | 
action\_result\.data\.\*\.data\.spamUrlSet\.\*\.url\_1\.protocol | string | 
action\_result\.data\.\*\.data\.spamUrlSet\.\*\.url\_1\.url | string |  `url` 
action\_result\.data\.\*\.data\.subjectSet\.\*\.subject | string | 
action\_result\.data\.\*\.data\.subjectSet\.\*\.totalCount | numeric | 
action\_result\.data\.\*\.data\.threatDetailURL | string |  `url` 
action\_result\.data\.\*\.data\.threatType | string | 
action\_result\.data\.\*\.success | boolean | 
action\_result\.summary\.threat\_label | string | 
action\_result\.summary\.threat\_type | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'on poll'
Action to ingest threats

Type: **ingest**  
Read only: **True**

<p>For the first poll, ingest all the threats during past number of days set in <b>first\_scheduled\_ingestion\_span</b>\. Subsequent polls ingest new or updated threats\. The threats are ordered in ascending order based on occurrence time\.<br>Only create CEFs for following types\:<br>\. executableSet<br>\. blockSet with impact of major or moderate</p><table><tbody><tr class='plain'><th>IOC</th><th>Artifact Name</th><th>CEF Field</th></tr><tr><td>Address IPv4</td><td>IP Artifact</td><td>destinationAddress</td></tr><tr><td>File</td><td>File Artifact</td><td>fileHashMd5, fileHashSha1, fileHashSha384, fileHashSha512, fileHashSha224, fileHashSha256, fileName, fileType, fileModificationTime</td></tr><tr><td>Host</td><td>Domain Artifact</td><td>destinationDnsDomain</td></tr><tr><td>URL</td><td>URL Artifact</td><td>requestURL</td></tr><tr><td>Threat Details</td><td>Threat Artifact</td><td>CofenseIntelligenceThreatId, threatType</td></tr></tbody></table>\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**container\_count** |  optional  | Maximum number of containers to ingest | numeric | 
**container\_id** |  optional  | Comma separated threat IDs | string | 
**start\_time** |  optional  | Parameter ignored in this app | numeric | 
**artifact\_count** |  optional  | Parameter ignored in this app | numeric | 
**end\_time** |  optional  | Parameter ignored in this app | numeric | 

#### Action Output
No Output