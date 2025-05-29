```
merge(traj1::NamedTrajectory, traj2::NamedTrajectory)
merge(trajs::AbstractVector{<:NamedTrajectory})
```

Returns a new NamedTrajectory object by merging `NamedTrajectory` objects. 

Merge names are used to specify which components to merge by index. If no merge names are provided, all components are merged and name collisions are not allowed. If merge names are provided, the names are merged using the data from the index provided in the merge names.

Joined `NamedTrajectory` objects must have the same timestep. If a free time trajectory is desired, setting the keyword argument `free_time=true` will construct the a component for the timestep. In this case, the timestep symbol must be provided. 

# Arguments

  * `traj1::NamedTrajectory`: The first `NamedTrajectory` object.
  * `traj2::NamedTrajectory`: The second `NamedTrajectory` object.
  * `free_time::Bool=false`: Whether to construct a free time problem.
  * `timestep_name::Symbol=:Δt`: The timestep symbol to use for free time problems.
  * `merge_names::Union{Nothing, NamedTuple{<:Any, <:Tuple{Vararg{Int}}}}=nothing`: The names to merge by index.
