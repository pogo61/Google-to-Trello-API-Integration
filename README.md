# SOA Software API HOOK
Put a nice company logo image here. 
Link to product documentation and product overview page
## Google Sheets API to Trello API integration
### About the API
- This integration API takes the name of an already defined Google Sheet spreadsheet and converts it to a Trello Board. The name of the spreadsheet becomes the Board name. The names of the worksheets, inside the spreadsheet, become the List names of the Board. The values of the first cell in a row in a worksheet becomes the name of a Card in the List.

### Pre-Reqs
- This uses the following API Hooks, that must be installed:
    + Google Sheets API Hook
    + Google Drive API Hook
    + Trello API Hook

### Getting Started Instructions
#### Download and Import
- Download GoogletoTrelloIntegration.zip
- Download the migrations.properties file, and edit it to replace the <replace this with your key> text with the "Container Key" of the ND or ND cluster in your target PM
- Login to PolicyManager  example: http://localhost:9900
- Select the root "Registry" organisation and click on the "Import Package" from the Actions navigation window on the right side of the screen
  - click on button to browse for the GoogletoTrelloIntegration.zip archive file 
  - make sure select the migrations.properties file 
  - click Okay to start the importation of the hook.
- this will create a *Google to Trello Integration* Organisation with the requisite artefacts needed to run the API.
- you can us the API as is calling http://"URL of the Listener of your ND"/google2trello_int/spreadsheet, or you can create an API in CM and expost it.
    - if you chose to create an API in CM, you must create a Service in your CM tenant which is a Virtual Service of the Google_To_Trello_Integration VS that was created by the import. Then Go to CM and create a API from an existing Service.

#### Verify Import
- Expand the services folder in the Google to Trello Integration you imported and find Google_To_Trello_Integration VS

#### Activate Anonymous Contract
- Expand the contracts folder in the Google to Trello Integration organisation you imported and find the "Anonymous" contract under the "Provided Contracts" folder
- click on the "Activate Contract" workflow activity in the righ-hand Activities portlet
- ensure that the status changes to "Workflow Is Completed"

#### Configure Security
- As per the listed Hooks procedures
- go to the Policies->Operational Policies->ProcessVariables policy in the Google to Trello Integration orgnisation
- click the modify link in the "XML Policy" tab
- change the values of the "auth.key" and "auth.token" elements to be those of your Tello API Hook credentials
- save the changes
- click the "Activate Policy" workflow action, on the right hand side of the policy details screen

#### Verify Connectivity
- Using  curl  -H "Content-Type: application/json" -d {"name":"Test"} http://"URL of the Listener of your ND"/google2trello_int/spreadsheet
    -  the value "Test" can be replaced with the name of your google sheets spreadsheet 
-  the response should be: 
    +  {
            "status": "Success",
            "detail": "Your Spreadsheet has been imported as a Trello Board"
        }

### Modify and Build
In the event you need to change the API Hook.   Here are the instructions to do so. 

### License
Put a link to an open source license

