### DiscordBot Workshop

This is a workshop for creating a Discord bot using the Discord.js library. 
This workshop is intended for beginners, and is written in a simple, easy-to-follow style.

## Table of Contents

- [Part I: Introduction](#part-i-introduction)
- [Part II: Setup](#part-ii-setup)
- [Part III: Ping Pong](#part-iii-ping-pong)

## Part I: Introduction

### What is Discord?

Discord is a free voice and text chat service for gamers that’s available on desktop and mobile. It’s used by over 200 million gamers worldwide, and it’s one of the fastest growing chat services on the internet.

### What is a Discord Bot?

A Discord bot is a program that runs on a server and listens for messages sent by users. When a user sends a message that matches a certain pattern, the bot can respond to it in a variety of ways. 
For example, a bot could respond to a command with a random cat picture, or it could play music in a voice channel. 

### Why should I make a Discord bot?

Discord bots are a great way to learn how to code. They’re fun to make, and they’re a great way to learn how to use a new programming language.

### What will we be making?

In this workshop, we’ll be making a simple Hangman game. The game will be played in a Discord server terminal.

## Part II: Setup

### Creating a Discord Bot

To create a Discord bot, you’ll need to create a new application on the [Discord Developer Portal](https://discord.com/developers/applications).

1. Go to the [Discord Developer Portal](https://discord.com/developers/applications) and click the “New Application” button.
2. Give your application a name, and click “Create”.
3. On the left side of the screen, click “Bot”.
4. Click “Add Bot” and confirm by clicking “Yes, do it!”.
5. Click “Copy” to copy your bot’s token. You’ll need this later.
6. Click “Bot” on the left side of the screen.
7. Unde "Privileged Gateway Intents", check the box labeled "Presence Intent", "Server Members Intent" and "Message Content Intent".
8. Click “OAuth2” on the left side of the screen.
9. Under the General tab, select "In-app Authorization" and then check the box labeled “bot” and "application.commands". 
10. Under the URL Generator tab, check the box labeled “bot” and "application.commands". 
11. Under “Bot Permissions”, check the box labeled Administrator. 
12. Copy the link that appears below “Scopes” and paste it into a new browser tab. Select the server you want to add the bot to, and click “Authorize”. 
13. Go back to the Discord Developer Portal and click “OAuth2” on the left side of the screen. 
14. Copy the Client ID and save it somewhere. You’ll need it later. 
15. Go to [repl.it](https://repl.it) and create a new repl. Select “Node.js” as the language. 
16. In the terminal, run `npm install discord.js`. This will install the Discord.js library, which we’ll be using to make the bot. 
17. Create a file called `index.js` and open it. 
18. Paste the following code into `index.js`:

```js
   const { Client, GatewayIntentBits } = require('discord.js');
   
   // Create a new client instance
   const client = new Client({
      intents: [
         GatewayIntentBits.Guilds,
         GatewayIntentBits.GuildMessages,
         GatewayIntentBits.MessageContent,
         GatewayIntentBits.GuildMembers,
         GatewayIntentBits.GuildMessageReactions,
         GatewayIntentBits.GuildPresences,
      ],
   });
   
   client.once('ready', () => {
      console.log(`Bot ${client.user.tag} is logged in!`);
   });
      
   client.login('your-token-goes-here');
```
19. Replace `your-token-goes-here` with the token you copied earlier. 
20. Click the green “Run” button in the top center of the screen to start the bot. If everything worked, you should see "Ready!" in the console. 
21. Congratulations! You’ve created your first Discord bot. 
22. Now, let’s make it do something.

## Part III: Ping Pong

Now that we’ve got the bot working, let’s make it do something useful. We’ll start by making a simple command that responds to a message.

1. In `index.js`, add the following code above the `client.login` line:

```js
   client.on('messageCreate', message => {
      try {
         if (message.author.bot) return;
         if (message.content.toLowerCase().includes('ping')) {
            message.channel.send('Pong');
         }
      } catch (err) {
         console.error(new Error(err));
      }
   });
```
2. Save the file and go back to the Discord server where you added the bot.
3. Send a message that says `ping`. If the bot responds with `Pong`, everything worked!
4. If the bot didn’t respond, make sure you copied the token correctly and that you invited the bot to the server.
5. If you’re still having trouble, ask for help in the [Discord.js server](https://discord.gg/bRCvFy9) or on the [repl.it Discord server](https://repl.it/discord).


## Part IV: Hangman

Now that we’ve got the bot responding to messages, let’s make it do something more interesting. We’ll start by making a simple Hangman game.

// missing code
