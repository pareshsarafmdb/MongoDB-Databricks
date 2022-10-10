# MongoDB-Databricks

## 1. Setup your Atlas cluster 

### Create Your MongoDB Atlas Cluster
If you already have a MongoDB Atlas account, log in and create a new Atlas cluster. If you do not have an account, you can set up a free cluster at the following URL: https://www.mongodb.com/cloud. Once your account is set up, you can create a new Atlas cluster by using the “+ New Cluster” dialog. MongoDB provides a free tier for Google Cloud.
![Create Cluster](/images/clustercreation.png)
Once you provide a cluster name and click on “create,” Atlas will take approximately five to seven minutes to create your Atlas cluster.

### Define Database Access
By default there are no users created in an Atlas cluster. To create an identity for our Spark cluster to connect to MongoDB Atlas, launch the “Add New Database User” dialog from the Database Access menu item.
![Database Access](/images/databaseaccess.png)

Notice that there are three options for authentication to MongoDB Atlas: Password, Certificate, and AWS IAM authentication. Select “Password,” and enter a username and password. Atlas provides granular access control: For example, you could restrict this user account to work only with a specific Atlas cluster or define the account as temporary and have Atlas expire within a specific time period.

### Defining Network Access
MongoDB Atlas does not allow any connection from the internet by default. You need to include MongoDB Atlas as part of a VPC peering or AWS PrivateLink configuration. If you do not have that set up with your cloud provider, you need to specify from which IP addresses Atlas can accept incoming connections. You can do this via the “Add IP Address” dialog in the Network Access menu. In this article, we will add “0.0.0.0,” allowing access from anywhere, because we don’t know specifically which IP our Databricks cluster will be running on.

![Network Access](/images/networkaccess.png)
MongoDB Atlas can also make this IP access list temporary, which is great for situations where you need to allow access from anywhere.

### Add Sample Data
Now that we have added our user account and allowed network access to our Atlas cluster, we need to add some sample data. Atlas provides several sample collections that are accessible from the menu item on the cluster.
![Load Data](/images/loaddata.png)


In this example, we will use the sales collection within the sample_supplies database.

![Connection String](/images/connstring.png)
Copy the MongoDB Atlas connection string by clicking on the Connect button and selecting “Connect your application.” Copy the contents of the connection string and note the placeholders for username and password. You will have to change those to your own credentials.






