# Chicken Game
Once, for a school project, I created a [chicken simulator](https://github.com/terckert/chicken-egg) that ran in jupyter notebooks. I wanted to try and bring that to life in a simple, flat world represented in ASCII characters.

## Table of Contents


## Requirements


## Running This Program


## Roadmap
1. Create a requirements.txt
1. 

## Design Thoughts
### Simulation Loop
My initial thought is to create a time tick system that controls updating the board state. A major concern is that with enough objects, it wont process game ticks fast enough and so it will slow down significantly as more objects are added to the board. This became true in my text only simulation, population booms wreaked havoc on processing time. I think that by lowering the scope and scaling in this simulation, this won't become an issue. These decision tree's were ma

###  The World
At its most basic, the game world will be an array of terrain objects. These objects will contain information such as:

Parameter | Description
--- | ---
**Population**|What chickens are currently are on this space.
**Max Population**|Maximum number of chickens that can be on a space at any given time. Being above this amount gives negative penalties to food generation.
**Food Available**|How much food is avaiable on a space
**Max Food**|The maximum amount of food available.
**Food Change Per X Ticks**|How much food it gains per x number of ticks
**Traversable**|Whether or not chickens can actually move onto this spot

They will also have to have different types, and potentially these types can mutate throughout the simulation. A few quick ideas:

Terrain Type|Description
--- | ---
Thick Grass|Full of bugs and plants that chickens can eat. Produces food faster than other terrain. When food avaiable grows above a certain amount, a space can become thick grass. This space can also impact those around it. If it is above a certain threshhold, the extra food can spill over into adjacent spots and help impact their growth. This will simulate bugs moving around and plants going to seed. Allows nest making. A nest will count towards maximum population by taking the ceiling of x eggs equal to 1 chicken.
Water|By nature impassable. Currently it would be viewed as infinite supply, but potentially will have to add depth in the future (no z-level). This impacts the growth of food in adjacent spaces. Chickens can drink from adjacent spaces.
Rocky Terrain|Impassable terrain. Provides no benefits to adjact spaces.
Thin Grass|Terrain that is below a certain level of food. Has reduced food growth. Does not allow for nesting.