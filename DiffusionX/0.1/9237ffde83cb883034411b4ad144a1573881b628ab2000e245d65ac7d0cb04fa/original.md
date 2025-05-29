````
`moment(traj::Trajectory, N::Int; τ=0.01, order::Int=1)`

The function to calculate the moment of the trajectory.

# Arguments
- `traj`: The trajectory.   
- `N`: The number of samples.
- `τ`: The time step.
- `order`: The order of the moment.

# Examples
```julia
using DiffusionX
sp = Bm()
traj = sp(10)
moment(traj, 1000; τ=0.01, order=2)
```
````
