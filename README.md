# CarND-Path-Planning-Project 
By Pablo Sauras Perez

## Submission code location
The submited code can be found in the **src** directory. In particular, the following files have been modified:
- main.cpp

## Important Depencencies
As stated in the project description, these are the important dependencies.
- cmake >= 3.5
- make >= 4.1 
- gcc/g++ >= 5.4

## Basic Build Instructions
As stated in th project description, from the project top directory:
- ```mkdir build && cd build```
- ```cmake .. && make```
-   ```./path_planning```

## Results. Valid trajectory
As it can be seen in the [results video](https://github.com/pablosaurasperez/CarND-Path-Planning-Project/blob/master/Path_Planing.mov):

- The car is able to drive at least 4.32 miles without incident.
- The car drives according to the speed limit.
- Max Acceleration and Jerk are not exceeded.
- Car does not have collisions.
- The car stays in its lane, except for the time between changing lanes.
- The car is able to change lanes.

##Reflection

The basic code is based on the guide provided in the lesson.

To create a smooth paths, splines where used (as indicated in the video tutorial of the lesson)

In order to evaluate if the behavior of the car, **d** and **s** where considered. The basic behavior is the following:

1. See if there are vehicles in our lane. This can be done by evaluating **d**.
2. If there are vehicles in our lane, see if we are at risk of collision. This can be done by evaluating **s** (gap evaluation).
3. If there is risk of collision (not enough gap to the other vehicle), set two flag: one to evaluate lane change, and the other one to reduce the speed.
4. **Evaluate lane change**. Here I evaluate if I have to keep in my lane, or I can change, depending on the gap with the vehicles that are in the lane that I want to switch to.
For example, if I am in lane 1, I evaluate the vehicles of lane 0. If there is not enough gap, I evaluate the vehicles in lane 2. If there is enough gap, I can switch to lane 2. Otherwise, I stay in lane 1 and reduce my speed.
If vehicle is in:
**Lane 0**. Evaluate change to Lane 1.
**Lane 1**. Evaluate change to Lane 0. If that one fails, evaluate Lane 2.
**Lane 2**. Evaluate change to Lane 1.

5. If I cannot change lanes, reduce speed.

