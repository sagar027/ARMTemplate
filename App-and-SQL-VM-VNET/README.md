# Deploy an Application & SQL Server Windows VM setup

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Fazure-quickstart-templates%2Fmaster%2F101-vm-simple-windows%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>
<a href="http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Fazure-quickstart-templates%2Fmaster%2F101-vm-simple-windows%2Fazuredeploy.json" target="_blank">
    <img src="http://armviz.io/visualizebutton.png"/>
</a>

This template allows you to deploy a combination of Windows Application VM in one subnet and a SQL Server 2017 in another subnet of a single Virtual Network (VNET). 
There is also a SQL Server configuration section which enforces SQL Server settings like log files, data files storage on disks.

This template is actually fusion of '101-vm-simple-windows(https://github.com/Azure/azure-quickstart-templates/tree/master/101-vm-simple-windows)' and	'101-sql-vm-new-storage(https://github.com/Azure/azure-quickstart-templates/tree/master/101-sql-vm-new-storage)'
The project is created in Visual Studio which lets you validate & deploy from Visual Studio 2019.

Alternative you can also deploy from CLI using :

Validate : az group deployment validate --name <deployment-name> -g <resorce-group> --template-file azuredeploy.json --parameters azuredeploy.parameters.json 
Deploy : az group deployment create--name <deployment-name> -g <resorce-group> --template-file azuredeploy.json --parameters azuredeploy.parameters.json 

If you are new to template deployment, see:

[Azure Resource Manager documentation](https://docs.microsoft.com/azure/azure-resource-manager/)

#Note: There is a standard NSG which is applied to the SQL Server VM. You might want to edit to the enforce the following :
	1. Allow traffic only from the application Subnet
	2. Open SQL Server port
	3. Allow RDP from your organization IP : whitelist on NSG. Better option is to remove the Public IP from SQL Server VM and deploy a jumpbox in a new subnet or create a site-to-site VM for mananging SQL Server VM
