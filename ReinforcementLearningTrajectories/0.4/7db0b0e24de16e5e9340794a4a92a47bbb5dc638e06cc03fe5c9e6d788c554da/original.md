```
Trajectory(container, sampler, controller)
```

The `container` is used to store experiences. Common ones are [`Traces`](@ref) or [`Episodes`](@ref). The `sampler` is used to sample experience batches from the `container`. The `controller` controls whether it is time to sample a batch or not.

Supported methoes are:

  * `push!(t::Trajectory, experience)`, add one experience into the trajectory.
  * `append!(t::Trajectory, batch)`, add a batch of experiences into the trajectory.
  * `take!(t::Trajectory)`, take a batch of experiences from the trajectory. Note that `nothing` may be returned, indicating that it's not ready to sample yet.
