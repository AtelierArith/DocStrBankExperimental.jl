````
`Trajectory(sp::StochasticProcess, T::Float64)` 

The type of stochastic process trajectories.

# Arguments
- `sp`: The stochastic process.
- `T`: The length of the trajectory.

# Examples
```julia
using DiffusionX
sp = Bm()
traj = sp(10)
```
````
