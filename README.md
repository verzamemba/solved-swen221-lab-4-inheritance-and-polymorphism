Download Link: https://assignmentchef.com/product/solved-swen221-lab-4-inheritance-and-polymorphism
<br>
The purpose of this lab is to get yet more experience with inheritance and polymorphism. In particular, you will use polymorphism to further develop a simple graphical adventure game.

<h1>An Adventure Game</h1>

In this lab you will be working with a very simple graphical adventure game. The adventure game world consists of Rooms connected together by Doors, and Items which are located in Rooms. The following illustrates two different views of the game:

Here, we can see two views of the game. In both cases, the player is in the “Great Hall”. In the second case, we can see that he/she has picked up a few items, including a “Gold Coin” and a “Key”.

The adventure game uses a simple text format to describe the game world, including the layout of rooms and the items they contain. This is implemented in the GameFile class, and an example is the following:

Room { name: “Dining Room” }

Room { name: “Lounge” }

Door { from: 0, to: 1 }

Coin { location: 1 }

This describes a game world with two rooms (the “Dining Room” and the “Lounge”) with one door connecting them. A gold coin can be found in the “Lounge”. Each line of a game file corresponds to a GameFile.Item organised in the following manner:

Kind { field: value, … }

Here, the Kind of object is “Room”, “Door”, “Coin”, “Key”, etc. Finally, field is the name of a field for the object in question, whilst value gives a value for that field (either a string or integer). There can be more than on field for any given object.

<h1>Getting Started</h1>

To get started, download the adventure.jar file from the course website and import this into an Eclipse project. The adventure game is provided with a Graphical User Interface (GUI), which you can run by right-clicking on AdventureGame and selecting “Run As−→Java Application”. You should find a game window similar to those above appears, and you can click on items in the game and perform actions.

<h1>Activity 1: Books</h1>

The aim of this activity is to extend the adventure game with a new Book item. Each Book should have a title, and be described like this in the GameFile format:

Room { description: “Dining Room” }

Book { location: 0, title: “Great Expectations” }

This describes a room called the “Dining Room” which contains a book entitled “Great Expectations”. The player should be able to Pickup and Drop a Book. The player should be able to Read a book when it is held in his/her inventory. Every book also has a description which is formed from the book’s title. Before a book is read, the description for the above book is simply:

A book entitled “Great Expectations”

After a book has been read, its description should be updated as the following illustrates:

A book entitled “Great Expectations”; it looks like it has been read

<strong>What to do. </strong>You should create a new class called Book which extends PickupableItem. You should also make a small modification to the AdventureGame class in order to create instances of your Book class from the GameFile.Items which describe them. Having done this, you should find that more of the tests in AdventureGameTests now pass.

<h1>Activity 2: Lockable Doors</h1>

The aim of this activity is to extend the adventure game with a new LockedDoor class which extends the Door class. Each LockedDoor should have a secret “code” so that keys with the corresponding code can can be used to unlock it. LockedDoors are described as follows in the GameFile format:

Room { description: “Dining Room” }

Room { description: “Hall” }

LockedDoor { from: 0, to: 1, code: 123 }

This describes a locked door connected the “Dining Room” with the “Hall”. The player should be able to Unlock and Lock the door, but only if he/she is carrying a key with the secret code “123”.

<strong>What to do. </strong>You should create a new class called LockedDoor which extends Door. You should also make a small modification to the AdventureGame class in order to create instances of your LockedDoor class from the GameFile.Items which describe them. Having done this, you should find that most of the tests in AdventureGameTests now pass.

<h1>Activity 3: Secret Buttons</h1>

The aim of this activity is to extend the adventure game with a new SecretButton class which implements Item. Each SecretButton should have a secret “code” so that, when it is pushed, any doors in the same room that have the same code are unlocked. SecretButtons are described as follows in the GameFile format:

Room { description: “Dining Room” }

Room { description: “Hall” }

LockedDoor { from: 0, to: 1, code: 123 }

SecretButton { location: 0, code: 123 }

This describes a locked door which connects the “Dining Room” with the “Hall”. The player should be able to Unlock the door by Pressing the SecretButton.

<strong>What to do. </strong>You should create a new class called SecretButton class which implements Item. You should also make a small modification to the AdventureGame class in order to create instances of your SecretButton class from the GameFile.Items which describe them. Having done this, you should find that all of the tests in AdventureGameTests now pass.