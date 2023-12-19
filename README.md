# flask_5_tailwind

This assignment will give you hands-on experience in video hosting, creating a Flask app styled with Tailwind CSS, and deploying it to a cloud platform. You'll leverage CDN services in Google Cloud or Azure to optimize video delivery, ensuring a seamless user experience for viewers worldwide.

## Video Creation or Procurement:

I chose to download a 30 second video called Tree Branches With Blue Sky Background 

## Cloud CDN & Video Hosting

Create A New Storage Account
- The video will be hosted on Azure's Content Delivery Network (CDN)
- On Azure, navigate to "Storage Accounts" in the drop down menu on the left side
- Create a new storage account
- Creare a subscription and resource group 
- Create a storage account name. I called the storage account flask5tailwind
- Select a region based on current location
- For performance, choose Standard
- For reduncancy, select Geo-redundant storage (GRS)
- Press Review and Create

Video Hosting
- Once the storage account is created, scroll down until you see "Security"
- In Security, enable "Allow Blob anonymous access" and then press Save
- Naviagte to the menu bar on the left side and click on "Data storage" and select "Containers"
- Create a new container and give it a name
- Under Anonymous access level, select Container
- Press Create
- In the newly created container, select upload
- You can drop or browse files to upload the video (.mp4)
- Click on Upload file
- Go to the newly uploaded video file and copy the URL. Paste it into a new tab in your browser
- Navigate back to the storage account and under "Security + networking", go to "Front Door and CDN"
- Here you will create a new endpoint
- For Service type, select Azure CDN
- Create new profile with a profile name and endpoint name. My profile name was tailwindassignment
- For Query string caching behavior, select Ignore Query String
- Press Create
- Click on your container name. Then click on your Endpoint
- You will now see a page that shows "Endpoint hostname" and "Origin hostname". Click on the URL for Endpoint Hostname.
 

- Going back to the URL pasted into the new tab from before, copy everything that comes after "-windows.net"
- Paste it into the Endpoint Hostname URL after the ".net"
- Press enter and refresh the page
- Be sure to save this URL as you will need to enter this in .html file 

## Flask App with Tailwind CSS

- Open Google shell and create a new <code>app.py</code> file
- Create a templates folder and within this folder, create an <code>index.html</code> file
- I used Professor Hants' [example](https://github.com/hantswilliams/HHA_504_2023/blob/main/WK5/example_app/templates/index_tailwind.html) code and made changes to the file
- Entered the following for <code>app.py</code> file:

## Cloud Deployment

- Deployed the Flask app on Azure App Service
- In the Google Shell terminal, install AZURE CLI with <code>curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash</code>
- Type <code>az</code>
- Then type <code>az login --use-device-code</code>
- Click on the URL provided which will open another tab to validate 
- Copy and paste the code provided with the URL
- Select your account
- Press "Yes" for the prompt "Are you trying to sign in to Microsoft Azure CLI?"
- Back in the terminal, type <code>az account list --output table</code>
- Locate the subscription that you will use and copy its "subscriptionID"
- Type <code>az account set --subscription [paste-subscriptionID]</code>
- Enter <code>az webapp up --name [name-of-webapp] --runtime PYTHON:3.9 --sku B1</code> in the Google Shell terminal. This will create a new webapp
- You can set the name of the webapp to your preference 
- This step of creating the web app can take a while to load
- On Azure, go to "App Services"
- Click on the newly created Wep app. The name here should be the same name you created in the terminal
- You will be redirected to the overview of the web app. You can find the link for your application under Default domain.
- Here is my web application: https://flask5tailwind.azurewebsites.net/

## Errors
- When deploying the app on local host through Google Shell, I got an error that the module __main__ could not be found. I tried deploying it through Visual Studio Code and it worked. I had no errors when deploying through Azure. 
