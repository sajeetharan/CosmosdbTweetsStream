Repository on cosmosdb explaining how to stream tweets from twitter using hashtags and store them in cosmosdb in real time. 

**Pre-Requisites Needed:**

I have the following in my local environment , hope you guys have already have😊, if not start setting up.

·                  Windows 10 OS
·                  Python 2.7
·                  Visual Studio Code or PyCharm (Any editor)
·                  Azure subscription

**Step 1: Install Python**
Hope you have already installed Python in your system , if not download and install from here. Once you install run the following command and see if its properly installed.

**Step 2: Install Tweepy and PyDocumentDB**
Install the following libraries needed. 
**Tweepy:**
Tweepy is a python package which is easy to use for accessing the twitter api. he API class provides access to the entire twitter RESTful API methods. Each method can accept various parameters and return responses. Install it with the following command,
>  Pip install tweepy  

If you get an error 'pip' is not recognized as an internal or external command. You should set the path as follows,

> C:\&gt;set PATH=%PATH%;C:\Python27\Scripts

Now you should be able to install it without any issue.

**Pydocumentdb:**
As mentioned above we will be storing the tweets in Azure’s cosmosdb , In order to do that we need the python package for cosmosdb which is pydocumentdb. Install it with the following command. 
> Pip install pydocumentdb

Now we have everything needed. Lets dive into coding.

**Step 3:**  Creating Listener to invoke the cosmosdb client.Create a listener named CosmosDBListener with the following methods

__init__ Initializes the client to make sure the connection is available.
On_data will load the data retrieved from the stream and write to the Cosmosdb.
On_error will throw if there is any network/key issues on console.

**Step 4: Stream data from twitter to cosmosDB**
Lets create the real code to connect to twitter and get the related tweets for several hashtags. We will need to authenticate with tweepy to get the twets, so pass the consumer secret and access secret to the api.
Set the connection policy for cosmosdb and create a client,
Next step is to read the tweets as follows , we are using .filter method to get tweets related to particular hashtags.

**Step 5: Creating configuration file**

Create the config file with the following values,

# Enter CosmosDB config details below.
masterKey = ' ' 
host = ' '

#Enter your database, collection and preferredLocations here.
databaseId = 'tweepyDemo'
collectionId = 'tweets'
preferredLocations = ''

# Enter twitter OAuth keys here.
consumer_key = ''
consumer_secret = ''
access_token = ''
access_secret = ''

**Steps 6:**
That;s it folks now if you goto command prompt and run the following command,

>  py cosmosdbdriver.py

You should see the tweets coming into your cosmosdb collection as follows.
