---
layout: post
section-type: post
has-comments: true
title: Build games challenge with AmazonQ
category: Tech
tags: [ "amazonq", "vibecoding", "duckhunt","python","AI" ]
---

## TL;DR

- Built Duck Hunt (retro game) with Amazon Q (AI code assistant) without any previous experience in game building
- Took me roughly 4hrs to build something from concept to mvp and though final product was not polished it was fully functional (my 8yr old thoroughly enjoyed playing it)
- Setup was a breeze and using cli to build the game felt intuitive and as well as convenient since I could see Amazon Q resolving errors and troubleshooting issue in real-time
- It wrote sensible git commits and took care of code versioning (in `trusted` mode, it automatically commited code to github after testing and debugging)
- Code available on [Github](https://github.com/nsarode/amzQ_duckhunt)


## The Challenge

When I first heard about Amazon's Build Games Challenge, I was intrigued but also skeptical. Vibe coding has become so hyped up, that anything related to it sounds sus to me. Could I, someone with **zero game development experience**, actually create a playable game? 

The challenge invited participants to use Amazon Q Developer CLI to build classic games, and I decided to test its capabilities by recreating Duck Hunt, the iconic shooting game from the 1980s. I have so many fond memories of playing this game during summer breaks and was excited to give this a whirl !

## Getting Started with Amazon Q

The [challenge webpage](https://community.aws/content/2y6egGcPAGQs8EwtQUM9KAONojz/build-games-challenge-build-classics-with-amazon-q-developer-cli) was well documented and had links to all the necessary steps to get set up. 
The process began with a simple conversation with Amazon Q through its CLI interface. I described what I wanted to build -- "a first-person duck hunting game built using `Ursina` python game-engine, with score tracking, time limits, and increasing difficulty". And asked it to create a file titled `duckhunt_instructions.txt` and "Add to it instructions and requirements that you know you will need to create a game with minimum additional input".  To my surprise, the file was thorough and gave me the impression that Amazon Q understood the concept pretty well with just that simple prompt. I opted for Ursina engine, because all example blog posts on the challenge page used `pygame` and figured `ursina` (listed by Google as one of the top 3 python based game-engines available) could be a good challenge to test it with. Nevermind that I have used neither of those game-engines ever in my life! 

## From Concept to Playable Game

Within minutes, Amazon Q had generated a complete Python codebase that included:
- A 3D environment with sky and ground
- Duck-like entities that move randomly through the game world
- A first-person camera with mouse aiming
- Shooting mechanics with hit detection
- Score tracking and high score system
- Game states (menu, playing, paused, game over)
- UI elements for all game screens

The most surprising part? When I ran the code, it actually worked! I was able to aim, shoot, and hit ducks flying across the screen. The score system tracked my hits and misses, and the game properly cycled through different states.

## Refining the Experience

Of course, the initial version wasn't perfect. I encountered a few issues that needed fixing:
1. **Mouse lag**: The mouse response was sluggish, making aiming difficult
2. **Window sizing**: The game launched in fullscreen with no easy way to resize
3. **Scoring bugs**: Hitting ducks didn't always increase my score

This is where Amazon Q truly impressed me. I simply described these issues conversationally, and it diagnosed and fixed each problem. For the mouse lag, it optimized the camera controller code. For window sizing, it added keyboard shortcuts (F9/F10 to resize, F11 for fullscreen). For the scoring bug, it fixed variable scope issues in the code.

## GitHub Integration

Amazon Q didn't just help with the game code. It also:
- Created a GitHub repository for the project
- Generated a comprehensive README with installation instructions
- Added Docker configuration for cross-platform compatibility
- Created appropriate badges and licensing for the repository
- Documented future improvement possibilities (I specifically asked it to add that)

## Strengths for Non-Developers

As someone who doesn't develop games, these strengths stood out to me:

- **Domain Knowledge** 

It understood game development concepts and patterns without me needing to explain them.

- **Complete Solutions** 

Rather than just code snippets, it provided end-to-end solutions including game logic, UI, and state management.

- **Debugging Capabilities**

When issues arose, it could diagnose and fix them based on error messages or my descriptions.

- **Project Management** 

It handled the entire software lifecycle from code creation to documentation and deployment configuration.

## Weaknesses and Limitations

Despite its impressive capabilities, I did notice some limitations:

- **Performance Optimization**

The initial code wasn't optimized for performance, requiring **several iterations** to fix mouse lag issues. It was ultimately Amazon Q that suggested that I introduce keyboard movements for optimum performance and that did the trick.

- **Asset Management** 

The game lacked proper asset handling, showing warnings about missing models and sounds, but no suggestions about fixing them. Once I did download the sound file and told it exactly where I want to use them (shooting ducks and ducks falling), it incorporated them without a hitch.

- **Error Handling** 

Some syntax errors made it into the code that had to be fixed later.

- **Testing Gaps**

 There was no automated testing included, which would be important for a larger project.

- **Architecture Decisions**

The code was monolithic rather than modular, which could limit extensibility.

## Recommendations for Improvement

Based on my experience, here are some recommendations for improving Amazon Q:

- **Performance Templates** 

Offer optimized templates for different types of applications, including games with responsive controls.

- **Asset Pipeline Integration**

Provide better guidance on asset management and perhaps even generate placeholder assets.

- **Architecture Patterns**

Suggest modular code organization from the start rather than requiring refactoring later.

- **Testing Generation**

Automatically (e.g. in trusted mode) include basic tests for critical functionality.

- **Interactive Debugging**

Improve the ability to interactively debug issues rather than requiring multiple back-and-forth exchanges.

## Screenshots and gameplay

There is a gameplay movie within the dedicated [github repo](https://github.com/nsarode/amzQ_duckhunt) within `gameplay_and_screenshots` directory (in case the webpage has rendering issues)

### Gameplay movie 

![Gameplay](https://github.com/nsarode/amzQ_duckhunt/raw/aaa43eae7cfe67a902f68c9082fce280c2c20816/gameplay_and_screenshots/gameplay.mov)

### Screenshots

![Screenshot 3](https://github.com/nsarode/amzQ_duckhunt/blob/aaa43eae7cfe67a902f68c9082fce280c2c20816/gameplay_and_screenshots/Screen%20Shot%2003.png?raw=true)

![Screenshot 1](https://github.com/nsarode/amzQ_duckhunt/blob/aaa43eae7cfe67a902f68c9082fce280c2c20816/gameplay_and_screenshots/Screen%20Shot%2001.png?raw=true)

![Screenshot 2](https://github.com/nsarode/amzQ_duckhunt/blob/aaa43eae7cfe67a902f68c9082fce280c2c20816/gameplay_and_screenshots/Screen%20Shot%2002.png?raw=true)

![Screenshot 4](https://github.com/nsarode/amzQ_duckhunt/blob/aaa43eae7cfe67a902f68c9082fce280c2c20816/gameplay_and_screenshots/Screen%20Shot%2004.png?raw=true)

## Conclusion

As someone with no game development experience, I was able to create a functional Duck Hunt game without writing any code myself. Amazon Q handled everything from game mechanics to GitHub setup. While there's room for improvement, the experience demonstrated how AI coding assistants are democratizing software development across domains.

I still think "vibe coding" is overhyped, but this experience helped me understand the use cases where it could truly be beneficial e.g. for non-coder stakeholder to design a rough first draft of their idea or problem. As any data scientist worth their salt knows, understanding the real requirements is half the battle. The most valuable personal insight for me was seeing how my data science skills— clear problem definition (making a requirements document), systematic debugging, and iterative improvement — transferred perfectly to this new domain when paired with Amazon Q's technical capabilities. This tool doesn't just write code; it bridges knowledge gaps and enables domain experts to create software and build solutions outside their specialization.

Amazon Q is not the only coding assistant on the market. So I am not going to **insist** on using one over the other (the jury is still out on that one). But I will make a strong case for the value of leverating coding assistants as a knowledge translator that helps specialists like me venture confidently into new technical territories.


