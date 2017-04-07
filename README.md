# Setting up a QA Build Machine

## Getting Started
This describes how to set up a QA Build machine for Android & iOS mobile devices on a macOS computer.  A macOS computer is required for iOS builds and can be used for Android builds as well.

### Passwords & Account Details
We will be setting up multiple accounts. Be sure to use the same account details everywhere, such as First Name, Last Name, Birthday, etc. Using different passwords for each account is recommended by most people.

### Email
Start with setting up an email account that will be used by the QA build machine. We recommend qabuild@<domain> and this post will assume qabuild.  It can be an alias that forwards to multiple developers, QA engineers and stake holders, or an individual email that has to be logged in to view.

### Gravatar
Just because it’s easier, add your account to gravatar.com and set an image to use as an avatar.  GitHub, Atlassian and many other sites go there to get the avatar for an email address.  Recommend that we set it to the company logo.

### Apple ID
Create an Apple ID account for the qabuild email address. Be sure to take notes of the details, such as birth date and security questions.  This will be used for Apple Developer,  iTunes Connect and downloading Xcode.  Be sure to set it up for the App Store as well, for downloading Xcode.  With the App Store it is fine to set it up with None as the payment type.  Have the account admin for the company’s Apple Developer account invite qabuild to the developer and iTunes Connect account, preferably as an admin.  Accept the invitation using the qabuild account.

### Google ID
Link the qabuild email to a Google Account if it isn’t already a Google Gmail account.  This will be used for Google Play Developer Console.  Have the account admin for the company’s Google Play Developer Console invite qabuild.  After linking the qabuild email, be sure to login to google.com using that email account.

### Source Control
Add the qabuild email as a user (read/write required) to GitHub.com, BitBucket.com or whichever source control site used.

## Computer
Personally, we’d recommend using a Mac Mini 2011 or earlier as they allow the memory and hard drive to be upgraded.  If we already have one, start by wiping it and installing macOS.


### macOS Account
Create a login account for the dedicated QA Build machine of qabuild.  Use the qabuild Apple ID and also setup Mail for the qabuild email address.

### Automatic Updates
Be sure to turn off Automatic Updates.  We don’t want to have everything setup and working well and then an update comes along and breaks everything.  We need to be in control of what updates occur.  Where this particularly matters is with Xcode and what versions of iOS we may need to support.  In System Preferences, click on App Store, turn off “Automatically check for updates”.

### Terminal
Search for Terminal and add it to the Dock.

### Hidden Files
Show hidden files in the Finder by executing the following command in the terminal:

    defaults write com.apple.finder AppleShowAllFiles TRUE
    killall Finder
    
### Finder Preferences
In Finder Preferences -> Sidebar, select qabuild.

### Text Editor
Download and install a text editor.  We prefer Sublime.  Install the text editor chosen and add it to the Dock.

### Source Control
Download the favorite source control tool, such as Source Tree by Atlassian from sourcetreeapp.com.

Add Source Tree to the Dock

### Xcode
Download Xcode from the App Store if the current version is required.  The qabuild Apple Id must be set up for the App Store.  Don’t be tempted to use an individual’s Apple Id.

If an older version of Xcode is required to build for older versions of iOS, then download from the Apple Developer archives.
Once downloaded, then Open Xcode.  Agree to all the agreements, etc.  Download the Command Line Tools for the version of Xcode and macOS installed, from Xcode -> Open Developer Tool -> More Developer Tools…

Add Xcode to the Dock.

### Android Studio
Install Android Studio.  Open Android Studio and setup per the web site instructions.  Downloading the components will take a while.
Ensure that all the required SDK’s and components are installed.
Add Android Studio to the Dock.

### JDK
Android Studio uses Java to build.  To build from Terminal, we need to select and install the most recent Java Development Kit 8.

### Gradle
Android Studio uses Gradle to build.  It normally uses a wrapper that downloads as needed.  To build from Terminal, it is best to install Gradle locally.  Go to gradle.org to download the required version (usually the latest).
We create a directory named bin off of the qabuild directory and copy the gradle directory there.  Using the text editor, create .bash_profile with the following:

    # Gradle
    export GRADLE_HOME=/Users/qabuild/bin/gradle-3.3
    export PATH=${PATH}:$GRADLE_HOME/bin
    
Verify that everything is set up correctly by closing any open Terminals, and opening a new Terminal.

    gradle -v
    
Should show the Gradle, Groovy, Ant, JVM and OS versions.
 
### Xamarin Studio
If Visual Studio or CSharp code is used, then install Xamarin Studio from xamarin.com
