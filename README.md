# Sentinel Project

![Sentinel Lab Screenshot](Sentinel1.png)
First, we are going to create a resource group, find resource group in Azure and click create. 

![Sentinel Lab Screenshot](Sentinel2.png)
Enter a name and click Review+create.

![Sentinel Lab Screenshot](Sentinel3.png)
Click Create.

![Sentinel Lab Screenshot](Sentinel4.png)
You should be able to find it in your Resource Manager, if you don’t see it, click on Refresh.

![Sentinel Lab Screenshot](Sentinel5.png)
Next step is to search for Virtual networks in your Azure search tab and click create. 

![Sentinel Lab Screenshot](Sentinel6.png)
Make sure the virtual network is in the same resource group and same region as the resource group. Click next. 

![Sentinel Lab Screenshot](Sentinel7.png)
Click next.

![Sentinel Lab Screenshot](Sentinel8.png)
Click next.

![Sentinel Lab Screenshot](Sentinel9.png)
Click next.

![Sentinel Lab Screenshot](Sentinel10.png)
Click create.

![Sentinel Lab Screenshot](Sentinel11.png)
Virtual network is created.

![Sentinel Lab Screenshot](Sentinel12.png)
Next step is to create a virtual machine. Search for Virtual Machines in the Azure search tab and then click create and select Virtual machine.

![Sentinel Lab Screenshot](Sentinel13.png)
Make sure it is in the resource group you just created and enter a name for the virtual machine.

![Sentinel Lab Screenshot](Sentinel14.png)
Choose a modern windows version and a relatively affordable virtual machine if available. If you are doing this purely for a lab, make sure to turn it off after completing the lab to avoid a big monthly fee. 

![Sentinel Lab Screenshot](Sentinel15.png)
Make sure to set a username and strong password for the Administrator account. And click Next. 

![Sentinel Lab Screenshot](Sentinel16.png)
Click next. 

![Sentinel Lab Screenshot](Sentinel17.png)
Make sure that you have your recent virtual network that you created selected. And then select the default subnet. Scroll down.

![Sentinel Lab Screenshot](Sentinel18.png)
Make sure this checkbox is selected. 

![Sentinel Lab Screenshot](Sentinel19.png)
Click Next.

![Sentinel Lab Screenshot](Sentinel20.png)
Click next.

![Sentinel Lab Screenshot](Sentinel21.png)
Under Monitoring, select disabled for boot diagnostics. And click Next.

![Sentinel Lab Screenshot](Sentinel22.png)
Click Next.

![Sentinel Lab Screenshot](Sentinel23.png)
Click Next

![Sentinel Lab Screenshot](Sentinel24.png)
Click Create

![Sentinel Lab Screenshot](Sentinel25.png)
Wait until your deployment is complete. 

![Sentinel Lab Screenshot](Sentinel26.png)
After deployment, go back to Resource Manager and click on your resource group. You should be able to see the newly created virtual machine along with the other add-ons.

![Sentinel Lab Screenshot](Sentinel27.png)
Click on the Resource that ends with nsg which deals with network security.

![Sentinel Lab Screenshot](Sentinel28.png)
Delete this RDP default rule.

![Sentinel Lab Screenshot](Sentinel29.png)
Go to settings on the left hand side and click on inbound security rules.

![Sentinel Lab Screenshot](Sentinel30.png)
Click Add

![Sentinel Lab Screenshot](Sentinel31.png)
Put a star on the Destination port ranges field so it allows any. 

![Sentinel Lab Screenshot](Sentinel32.png)
Give the rule a name and click add. 

![Sentinel Lab Screenshot](Sentinel33.png)
You should be able to see the rule in the inbound security rules page. 

![Sentinel Lab Screenshot](Sentinel34.png)
Go to the Virtual Machines page on Azure and click on your Virtual machine.

![Sentinel Lab Screenshot](Sentinel35.png)
Copy the Public IP address. 

![Sentinel Lab Screenshot](Sentinel36.png)
Open Remote Desktop on your start menu and connect to the public IP address.

![Sentinel Lab Screenshot](Sentinel37.png)
Should prompt a username and password field. Enter the one you gave it when you created the Virtual Machine.

![Sentinel Lab Screenshot](Sentinel38.png)

![Sentinel Lab Screenshot](Sentinel39.png)
Make sure it is your Virtual Machine you are connecting to, that way it does not matter if the certificate is not from a trusted authority. Say yes.

![Sentinel Lab Screenshot](Sentinel40.png)
And we are in.

![Sentinel Lab Screenshot](Sentinel41.png)
Next step is to disable the firewall settings. Go search for wf.msc and open it.

![Sentinel Lab Screenshot](Sentinel42.png)
Click on windows defender firewall properties.

![Sentinel Lab Screenshot](Sentinel43.png)
Under domain profile turn the firewall state off.

![Sentinel Lab Screenshot](Sentinel44.png)
Under private profile turn the firewall state off.

![Sentinel Lab Screenshot](Sentinel45.png)
Under public profile turn the firewall state off.

![Sentinel Lab Screenshot](Sentinel46.png)
Click Apply and then ok to close.

![Sentinel Lab Screenshot](Sentinel47.png)
Do a quick ping to the virtual machine from your own computer to see if you are able to send and receive signal, so you know it is in the public network. 

![Sentinel Lab Screenshot](Sentinel48.png)
Go back to virtual machines and search for event viewer.

![Sentinel Lab Screenshot](Sentinel49.png)
Click on windows log on the top left.

![Sentinel Lab Screenshot](Sentinel50.png)
Click on security.

![Sentinel Lab Screenshot](Sentinel51.png)
We are specifically looking for event id 4625 which is failure to log in.

![Sentinel Lab Screenshot](Sentinel52.png)
If you click on an individual log, you can observe more information about the failed attempt.

![Sentinel Lab Screenshot](Sentinel53.png)
You can filter it out by clicking on the top right filter icon and searching specifically for event id 4625.

![Sentinel Lab Screenshot](Sentinel54.png)
Go back to Azure and search for Log Analytics workspaces.

![Sentinel Lab Screenshot](Sentinel55.png)
Click create

![Sentinel Lab Screenshot](Sentinel56.png)
Make sure it is using the same resource group your lab is in and give it a name. Also make sure it is in the same region. 

![Sentinel Lab Screenshot](Sentinel57.png)
Click create.

![Sentinel Lab Screenshot](Sentinel58.png)
Make sure the deployment is complete.

![Sentinel Lab Screenshot](Sentinel59.png)
After that search for Microsoft Sentinel on Azure and click create.

![Sentinel Lab Screenshot](Sentinel60.png)
Add the log workspace you just created.

![Sentinel Lab Screenshot](Sentinel61.png)
Once your sentinel instance is created go to content management. 

![Sentinel Lab Screenshot](Sentinel62.png)
Then go to content hub.

![Sentinel Lab Screenshot](Sentinel63.png)
Search for Windows Security Event and click install.

![Sentinel Lab Screenshot](Sentinel64.png)
After installation, click on manage. 

![Sentinel Lab Screenshot](Sentinel65.png)
Select Windows Security Events via AMA and then click on open connector page.

![Sentinel Lab Screenshot](Sentinel66.png)
Click Create data collection rule.

![Sentinel Lab Screenshot](Sentinel67.png)
Make sure you give the data collection rule a name and select your resource group used for the lab. Click next: resources after. 

![Sentinel Lab Screenshot](Sentinel68.png)
Expand and check everything under the Azur subscription including your resource group and virtual machine. And click next: collect after. 

![Sentinel Lab Screenshot](Sentinel69.png)
Make sure all security events is selected and then click Next:review + create.

![Sentinel Lab Screenshot](Sentinel70.png)
Click create. 

![Sentinel Lab Screenshot](Sentinel71.png)
Go back to your virtual machine in azure and click under the settings tab and then click extension, you should be able to see the extension Azure monitor windows agent. 

![Sentinel Lab Screenshot](Sentinel72.png)
Go back to the log analytics workspaces and click on your workspace from before. 

![Sentinel Lab Screenshot](Sentinel73.png)
Click on Logs and change the mode on the right side to KQL mode.

![Sentinel Lab Screenshot](Sentinel74.png)
Type in SecurityEvent for the first line and click Run. You should be able to see the failed login events at the bottom. 

![Sentinel Lab Screenshot](Sentinel75.png)
Enter 
| where EventID == 4625
| project TimeGenerated, Account, Computer, EventID, Activity, IpAddress
Below SecurityEvent to filter search further. Wait a half an hour to a couple hours and wait for some failed login attempts before running another search if you do not see any activity. You can do a quick google search of the IP address and find out where it is, for example, the first one listed in my search is from Chile.

![Sentinel Lab Screenshot](Sentinel76.png)
https://drive.google.com/file/d/13EfjM_4BohrmaxqXZLB5VUBIz2sv9Siz/view?usp=sharing
Post this link below and download the list. You will need it for later. 

![Sentinel Lab Screenshot](Sentinel77.png)
Go back to your sentinel instance in Azure and go under configuration and click watchlist. Click on the “go to defender portal” link. 

![Sentinel Lab Screenshot](Sentinel78.png)
Click new.

![Sentinel Lab Screenshot](Sentinel79.png)
Put geoip as name and alias. 

![Sentinel Lab Screenshot](Sentinel80.png)
Upload the file you just downloaded and also put network as the searchkey.

![Sentinel Lab Screenshot](Sentinel81.png)
Click Next.

![Sentinel Lab Screenshot](Sentinel82.png)
Click Create.

![Sentinel Lab Screenshot](Sentinel83.png)
Wait a while till upload finishes.

![Sentinel Lab Screenshot](Sentinel84.png)
Done.

![Sentinel Lab Screenshot](Sentinel85.png)
Go to your Microsoft Sentinel instance. Go under threat management and click workbooks. Did should give you an option to go to the defender portal. 

![Sentinel Lab Screenshot](Sentinel86.png)
Click add workbook. 

![Sentinel Lab Screenshot](Sentinel87.png)
Remove former elements. 

![Sentinel Lab Screenshot](Sentinel88.png)
Click add and then select add data source + visualization.

![Sentinel Lab Screenshot](Sentinel89.png)
Go to advance editor.

![Sentinel Lab Screenshot](Sentinel90.png)
Delete the previous script and Copy and paste the script below and click apply.

https://drive.google.com/file/d/1ErlVEK5cQjpGyOcu4T02xYy7F31dWuir/view

{
	"type": 3,
	"content": {
	"version": "KqlItem/1.0",
	"query": "let GeoIPDB_FULL = _GetWatchlist(\"geoip\");\nlet WindowsEvents = SecurityEvent;\nWindowsEvents | where EventID == 4625\n| order by TimeGenerated desc\n| evaluate ipv4_lookup(GeoIPDB_FULL, IpAddress, network)\n| summarize FailureCount = count() by IpAddress, latitude, longitude, cityname, countryname\n| project FailureCount, AttackerIp = IpAddress, latitude, longitude, city = cityname, country = countryname,\nfriendly_location = strcat(cityname, \" (\", countryname, \")\");",
	"size": 3,
	"timeContext": {
		"durationMs": 2592000000
	},
	"queryType": 0,
	"resourceType": "microsoft.operationalinsights/workspaces",
	"visualization": "map",
	"mapSettings": {
		"locInfo": "LatLong",
		"locInfoColumn": "countryname",
		"latitude": "latitude",
		"longitude": "longitude",
		"sizeSettings": "FailureCount",
		"sizeAggregation": "Sum",
		"opacity": 0.8,
		"labelSettings": "friendly_location",
		"legendMetric": "FailureCount",
		"legendAggregation": "Sum",
		"itemColorSettings": {
		"nodeColorField": "FailureCount",
		"colorAggregation": "Sum",
		"type": "heatmap",
		"heatmapPalette": "greenRed"
		}
	}
	},
	"name": "query - 0"
}

![Sentinel Lab Screenshot](Sentinel91.png)
Scroll to bottom and press done editing. 

![Sentinel Lab Screenshot](Sentinel92.png)
You should get something cool like this. 

![Sentinel Lab Screenshot](Sentinel93.png)
You can select a circle on the map and see more specifics. 
