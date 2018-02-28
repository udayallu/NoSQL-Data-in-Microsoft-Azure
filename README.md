# NoSQL-Data-in-Microsoft-Azure
We will explore **NoSQL** data using the **Cosmos DB** service – a highly scalable data store for key-value table, JSON document, and graph data.
## Working with a Key-Value Table
you will use Cosmos DB to work with **key-value data** in **Azure Table storage**
### Provision Azure Cosmos DB for Table Storage
To get started, you must provision an **instance of Azure Cosmos DB**.
### Steps:
1. In the Microsoft Azure portal, in the menu, click New. Then in the Databases menu, click **Azure Cosmos DB**.
2. In the Azure Cosmos DB blade, enter the following settings, and then click Create:
- ID: Enter a unique ID for your Cosmos DB service
- API: Table (key-value)
- Subscription: Select your Azure subscription
- Resource Group: Select the resource group you created in the previous labs
- Location: Select any available region
- Pin to dashboard: Unselected
### Create a Table
**Cosmos DB** supports Azure Table Storage for **key-value pairs**.
1. View the blade for the Cosmos DB instance you created for table storage, and click the Data Explorer tab.
2. In the Data Explorer, click New Table.
3. In the Add Table pane, enter the following details and click OK:
- Table Id: Employees
- Storage capacity: Fixed (10 GB)
- Throughput: 2000
4. In the **Data Explorer**, expand the new **Employees** table and select **Entities**.
5. In the **Entitie**s tab, click **Add Entity**.
6. In the Add Table Entity pane, Enter the following property values (clicking + Add Property as required) and then click Add Entity.
### Query a Table
Now that you have some data in your table, you can query it.
1. In the Entities pane, click Add new clause.
2. Set the following properties for the clause:
3. Click  Run to run the query and apply the filter. Note that only the rows where the PartitionKey value is “Marketing” are returned.
4. Click Add new clause to add a second clause to the query.
## Exercise 2: Working with Documents
In this exercise, you will use Azure Cosmos DB to work with a collection of JSON documents.
### Provision Azure Cosmos DB for Document Storage
To get started, you must provision an instance of Azure Cosmos DB.
1. In the Microsoft Azure portal, in the menu, click **New**. Then in the **Databases** menu, click **Azure Cosmos DB**.
2. In the Azure Cosmos DB blade, enter the following settings, and then click Create:
- ID: Enter a unique ID for your Cosmos DB service
- API: SQL
- Subscription: Select your Azure subscription
- Resource Group: Select the resource group you created in the previous labs
- Location: Select any available region
- Pin to dashboard: Unselected
3. In the Azure portal, view Notifications to verify that deployment has started. Then wait for the Cosmos DB service to be deployed (this can take a few minutes.)
## Create a Document Collection
**Cosmos DB** supports Document DB databases for collections of **JSON** documents
1. View the blade for the Cosmos DB instance you created for document storage, and click the **Data Explorer** tab.
2. In the Data Explorer, click **New Collection**.
4. In the Data Explorer, expand the new **EmployeeDocs collection** and select **Documents**.
5. In the **Documents** tab, click **New Document**.
6. In the document editor, create the following JSON document and then click Save:
```
{
"id": "1",
"dept": "Marketing",
"email": "dan@contoso.com",
"firstName": "Dan",
"lastName": "Drayton"
}
```
7. Click New Document and create a second document with the following JSON:
```
{
"id": "2",
"dept": "Marketing",
"email": "joann@contoso.com",
"firstName": "Joann",
"lastName": "Chambers"
}
```
8. Click New Document and create a third document with the following JSON:
```
{
"id": "3",
"dept": "Human Resources",
"email": "rosie@contoso.com",
"firstName": "Rosie",
"lastName": "Reeves"
}
```
### Query a Document Collection
Now that you have a collection of documents, you can query it:
1. In the Data Explorer, click New SQL Query.
2. In the Query 1 tab, modify the existing query to use the following SQL statement:
```SELECT c.firstName, c.lastName
FROM c
WHERE c.dept = 'Marketing'
```
3. Click  Execute Query to run the query. Note that only the documents for Dan Drayton and Joann Chambers are returned.

## Exercise 3: Working with a Graph
In this exercise, you will use Azure Cosmos DB to work with a Graph.
### Provision Azure Cosmos DB for Graph Storage
To get started, you must provision an instance of **Azure Cosmos DB**.

1. In the Microsoft Azure portal, in the menu, click **New**. Then in the **Databases** menu, click **Azure Cosmos DB**.
2. In the **Azure Cosmos DB** blade, enter the following settings, and then click Create:
- ID: Enter a unique ID for your Cosmos DB service
- API: Gremlin (graph))
- Subscription: Select your Azure subscription
- Resource Group: Select the resource group you created in the previous labs
- Location: Select any available region
- Pin to dashboard: Unselected
3. In the **Azure portal**, view Notifications to verify that deployment has started. Then wait for the **Cosmos DB service** to be deployed (this can take a few minutes.)
### Install Node.JS and Run a Script to Populate the Graph
Although you can create vertices in a graph using the Data Explorer interface in the Azure portal, it lacks the ability to edit vertices and create edges between them. You will therefore use a Node.JS script to populate your graph.
