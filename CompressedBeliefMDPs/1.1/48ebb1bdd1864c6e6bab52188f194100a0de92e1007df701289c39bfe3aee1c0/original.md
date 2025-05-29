```
CircularMaze(n_corridors::Integer, corridor_length::Integer, discount::Float64, r_findgoal::Float64, r_timestep_penalty::Float64)
CircularMaze(n_corridors::Integer, corridor_length::Integer; kwargs...)
CircularMaze()
```

A POMDP representing a circular maze environment.

# Fields

  * `n_corridors::Integer`: Number of corridors in the circular maze.
  * `corridor_length::Integer`: Length of each corridor.
  * `probabilities::AbstractArray`: Probability masses for creating von Mises distributions.
  * `center::Integer`: The central position in the maze.
  * `discount::Float64`: Discount factor for future rewards.
  * `r_findgoal::Float64`: Reward for finding the goal.
  * `r_timestep_penalty::Float64`: Penalty for each timestep taken.
  * `states::AbstractArray`: Array of all possible states in the maze.
  * `goals::AbstractArray`: Array of goal states in the maze.

# Example

```julia
using CompressedBeliefMDPs

n_corridors = 8
corridor_length = 25
maze = CircularMaze(n_corridors, corridor_length)
```
