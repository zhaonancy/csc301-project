# The Teacher App/ YBB

## Description 
 * The Teachers can use this app to see the Mental Health Resources and Perks with clicks away.
 * They can also see the posts made by other users or make post themself.
 * The Challenge provides them ways to earn prizes.
 * The Chat companion app allows them to chat with Counselors.

## Key Features

For different layers, the key features are shown below:
 * For iOS app, here are the main key features: (only for teachers and counsellors to login and register)
 * Login
    * Register
    * Teachers can view Self Profiles
    * Teachers can view Resources
    * Teachers can view Perks
    * Teachers can view Newsfeed
    * Teachers can view Challenges

 * For the web app, here are the main key features: (only for administrators)
    * After logging in from the website, administrators can have access to several functions to modify different types of data saved in MongoDB (check the instruction for current admin accounts)
        * Currently focus on adding and deleting data, function to modify a specific data will be implemented in the later phase
    * Admin can view and delete daily challenge, add a challenge
    * Admin can view and delete perks, add perks
    * Admin can view and delete mental health resources, add a resource
    * Admin can view and delete newsfeed posts by teachers
    * Admin can view information of teachers and mental health counsellors, delete an account or add an account(teacher and counsellor for now).
    * Note that currently delete can display immediately on the web application while add can not, but it has changed the database so need login again to see new data, will implement a way to show real-time add and modification later.

 * For the back-end, here are the main key features: (Note: You can check each API functionalities in detail from sever.js)
    * Allow uploading images including jpeg, jpg, png from the front end and save it on the database. 
        * Note: Since the storage of free MongoDB is only 512MB, please don't upload large images. Although there are no size limitations for uploading files, please try to compress images and upload images smaller than 512KB.
    * Allow system maintainers to switch store image filename mode, one is storing the file's own original name (can be used for saving some important images such as company Logo like \<Logo.png\>, which is already stored in the database); the other is storing hashed fileNames to ensure that there are no duplicate fileNames. (can be used for all other users to upload their own images)
    * Allow reading images through /image/\<fileName + fileName Extension\>. For example, /image/Logo.png
        * Note: Since all images are stored in the database, so reading images may have network transmission delay, especially for large images
    * Allow deleting images through file's ObjectId from MongoDB
        * Note: Images will be permanently deleted from the database and cannot be recovered
    * Allow system maintainers to add or remove default administrators, these APIs will never be called from the front end.
    * Allow administrators to log in, add or delete or modify teachers, counsellors, challenge types, newsfeeds, perks, resources these APIs will be called from the front end.
        * Note: There are still small bugs on modified information (patch APIs), we will fix them soon.
    * Allow teachers and counsellors to sign up, log in.
    * All passwords are dynamically encrypted by hashing, so no one can know your password even if the database is compromised by others.
    * Allow front end to show all information about ChallengeType // Newsfeed // Perk // Resource
 * For database (MongoDB), here are the main key features:
    * There are 9 collections including 3 users' collections and 4 objects' collections and also 2 collections for saving images.
        * 3 different users' collections: administrators // teachers // counsellors
        * 4 objects' collections: challengetypes // newsfeeds // perks // resources
        * 2 collections for saving images: upload.chunks // upload.files
        
## Instructions
 
To access the web application, check the link of Heroku at the Deployment section, from the landing page admin can log in to access the functions available. By clicking each card, the admin will be directed to the corresponding page. Every piece of data will be presented by a card, click the card to delete or use the button on each page to add data.

To access the mobile application, ensure you have React Native on your computer. Check  https://reactnative.dev/docs/environment-setup. Also, you need to have an iOS or Android emulator on your computer. After this, you need to build the app. First, change directory into the /TheTeacherApp_ReactNative/TheTeacherApp, then run npm install, followed by npm start or expo start if you use Mac. Press a for android emulator or i for ios emulator. Scanning the QR Code in the cli will let you view the app on an Android Phone.


 Temporarily, there are 3 different user types and 4 different object types in our project:
 * 3 user types are Teacher // Counsellor // Administrator:
    * For administrators, their accounts are pre-created, and we set 2 accounts for testing. 
        * email: admin@admin.com, password: admin
        * email: admin2@admin2.com, password: admin2
            * Note: Administrators can log in through web APP. For all administrators, they can access to almost all the functionalities, even change passwords of teachers and counsellors. The system maintainer could add or remove default administrators through APIs, these APIs will never be called from front end.
    * For teachers, their accounts are not pre-created, but we have already set 2 accounts for testing.
        * email: teacher@teacher.com, password: teacher
        * email: teacher2@teacher2.com, password: teacher2
            * Note: Teachers can login and register new accounts through iOS APP.
    * For counsellors, their accounts are not pre-created, but we have already set 2 accounts for testing.
        * email: counsellor@counsellor.com, password: counsellor
        * email: counsellor2@counsellor2.com, password: counsellor2
            * Note: Counsellors can login and register new accounts through iOS APP. 
 * 4 objects types are ChallengeType // Newsfeed // Perk // Resource:
    * For challenge types, there are 2 pre-created challenges for testing. Administrators can add or remove challenge types through the web app. Teachers and counsellors can access different challenges but have no permission to edit them.
        * Yoga Challenge
        * Mental Health Counselling
    * For newsfeeds, there are 2 pre-created newsfeeds for testing. Administrators can add or remove challenges types through web app. Teachers and counsellors can add, remove newsfeeds through iOS APP.
        * teacher newsfeed
        * counsellor newsfeed
    * For perks, there are 2 pre-created perks for testing. Administrators can add or remove perks through the web app. Teachers and counsellors can access different perks but have no permission to edit them.
        * Amazon coupon
        * Bestbuy iphone coupon
    * For resources, there are 2 pre-created perks for testing. Administrators can add or remove resources through the web app. Teachers and counsellors can access different resources but have no permission to edit them.
        * Resource 1
        * Resource 2
 
 Also, there may be some special functionalities for the next deliverable:
 * Teachers and counsellors can follow each other. (not completed yet)
 * Teachers and counsellors can chat with each other. (not completed yet)
 * Allow modifying information about 3 different users and 4 different objects. (APIs have completed, but small bugs exists)
 * Upload and modify users own profile picture. (not completed yet)
 * Creating newsfeeds can upload images for cover at the same time. (not completed yet)
 * Show images-cover for challenge types, newsfeeds, resources. (not completed yet)
 * Make UI closer to <the teacher app> official requirements. 
 
 
 ## Development requirements
 * In order to test the app on the iOS emulator, you will need a Mac. You may test the app on Android devices but it is not optimized for it.
 #### Additional installation
 Please go to https://nodejs.org/en/ to install nodeJs the latest LTS version
  ##### Note: If you wish to set this up on their machine or a remote server, please ensure your nodeJs is later than 16.13.0 LTS version and npm later than 8.1.0. School lab are not available to run this project since nodeJs is not later than 16.13.0 LTS version
 
 #### Build web app and test locally
 Use these codes in terminal to get start: (Use Port 5000, i.e. http://localhost:5000/)
 ```
 $ npm run setup
 ```
 The code above is equivalent to: (You can also use this code below, skip it if you have already run \<npm run setup\>)
 ``` 
 $ cd client
 $ npm install
 $ cd ..
 $ npm install
 ```          
 Then, you just need to run the code below:
 ```
 $ npm run build-run
 ```

 #### Build mobile app and test locally 
 Make sure you have React Native and emulator on your computer first.
 ```
 $ cd deliverable-2/TheTeacherApp_ReactNative/TheTeacherApp
 $ npm install
 ```          
 If you are using PC:
 ```
 $ npm start
 ```
 If you are using Mac:
 ```
 $ expo start
 ```


 ## Deployment and Github Workflow


* GitHub Deploy: The GitHub repository has been connected to Heroku. The backend and web frontend will be automatically deployed to Heroku when commits have been made.

* We first each fork the original repository and work in our private ones.
* When we hit a milestone (e.g., a big feature achieved), we try to contribute to the main branch.
* Usually, if there are no conflicts, we will make a pull request and contribute to the master branch.
* If there are conflicts, we discuss and check which file is causing the trouble.
* The backend and front end use different folders, which prevents unnecessary conflicts.


 #### Deployment
  * Heroku Link:
    https://intense-savannah-67936.herokuapp.com/
 ## Licenses 

 * No License (Our partner would like us to not share the code or software, thus no license applies)


