```
Pathfinding
```

Submodule containing functionality for path-finding based on the A* algorithm. Currently available for [`GridSpace`](@ref) and [`ContinuousSpace`](@ref). Discretization of [`ContinuousSpace`](@ref) is taken care of internally.

You can enable path-finding and set its options by creating an instance of a [`Pathfinding.AStar`](@ref) struct. This must be passed to the relevant pathfinding functions during the simulation. Call [`plan_route!`](@ref) to set the destination for an agent. This triggers the algorithm to calculate a path from the agent's current position to the one specified. You can alternatively use [`plan_best_route!`](@ref) to choose the best target from a list. Once a target has been set, you can move an agent one step along its precalculated path using the [`move_along_route!`](@ref) function.

Refer to the [Maze Solver](https://juliadynamics.github.io/AgentsExampleZoo.jl/dev/examples/maze/), [Mountain Runners](https://juliadynamics.github.io/AgentsExampleZoo.jl/dev/examples/runners/) and [Rabbit, Fox, Hawk](https://juliadynamics.github.io/Agents.jl/stable/examples/rabbit_fox_hawk/) examples using path-finding and see the available functions below as well.
