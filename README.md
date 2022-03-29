# Azure Resource Naming Calculator

The Azure Resource Naming Calculator is a a macro-enabled Excel spreadsheet that allows you to create formatting expressions to test your naming convention against resource name lengths and formatting requirements. 

It's based on https://github.com/dotnetnate/blog/blob/master/src/namingcalculator/README.md


### Getting Started
To get started, open the "Resource Names" tab and begin by populating the Organization Name, Project/Product Name and Name Format columns. While the first two are obvious, the Name Format is the key value of the sheet. This is what allows names to be computed based on the various components of the resource information. 

To create an expression, simply enter any text along with the replacement tokens in the format of {token} within the expression. Valid tokens include:

* productName - The name of the product or project, sourced from Resource Names!D3
* component - The name of the component, sourced from the "Component(Application/Workload)" column
* organizationName - The name of the organization, sourced from Resource Names!D2
* environmentName - The full name of the environment - resolved with  VLOOKUP and down based on the value in the Environments sheet.
* environmentShortCode - The short code of the environment - resolved with  VLOOKUP and down based on the value in the Environments sheet.
* environmentLongCode - The long code of the environment - resolved with  VLOOKUP and down based on the value in the Environments sheet.
* AzureRegion - Name of the region - resolved with  VLOOKUP and down based on the value in the Azure Region sheet.
* AzureRegionShortCode - Short Code of Region based on the value in the Azure Region sheet.
* azureServiceAbbreviation - The full resource type name - resolved with  VLOOKUP and down based on the value in the Resources sheet.


For example, with *{azureServiceAbbreviation}{component}-{EnvironmentLongCode}-{AzureRegion}-{Incremental}* :


![image](https://user-images.githubusercontent.com/39990341/158825007-22ce383e-37ce-4712-afa9-3fb5e35af11f.png)



You can modify sheets as you need

The validation lists in the ResourceNAmeLimits sheet will pick it up. These are regular expressions which you can test at [Regex 101](https://regex101.com/)  
