<h1> Sleep Tracker</h1>

<h2>Overview</h2>
>Having enough sleep is crtical for everybody to re-energize, especially for college students. This website, Sleep Tracker, helps users to keep a log of their sleep time. Users can register and login, which allows the Sleep Tracker to keep a personal record of how many hours of sleep each user gets. Registered users can then choose to view their sleep log by weeks, months, or years, if they keep log on their sleeping schedule. 

<h2>Data Model</h2>

  First draft schema:
  
    // users
    // * our site requires authentication...
    // * so users have a username and password
    // * they also can have 0 or more lists to keep track of loved ones' sleep schedules too
    // * (even though I think it is weird to log on others' sleep schedule )
    var User = new mongoose.Schema({
        //username, password provided by plugin
        lists:  [{ type: mongoose.Schema.Types.ObjectId, ref: 'List' }]
    });
  
  
    // an sleep (or group of the same sleep in a sleep list)
    // * includes the bedTime and wakeupTime 
    var Sleep = new mongoose.Schema({
        badTime: {type: Number, required: true},
        wakeupTime: {type: Number, required: true}
    },{
        _id: true    
    });
    
    // a sleep list
    // * each list must have a related user
    // * a list can have 0 or more items
    var List = new mongoose.Schema({
        user: user: {type: mongoose.Schema.Types.ObjectId, ref:'User'},
        createdAt: {type: Date, required: true},
        sleep: [Sleep]
    })
    
<h2>Wireframes</h2>

/home -homepage where users can choose to register or login

![Alt text](final-project/public/images/image1.jpg?raw=true "homepage")


/home/login -authetication
![Alt text](final-project/public/images/image2.jpg?raw=true "homepage")


/home/regist -create a new account
![Alt text](final-project/public/images/image3.jpg?raw=true "homepage")

/home/sleeplog -users update their sleeping time
![Alt text](final-project/public/images/image4.jpg?raw=true "homepage")


