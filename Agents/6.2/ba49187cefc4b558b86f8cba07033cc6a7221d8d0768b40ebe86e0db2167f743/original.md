```
move_agent!(agent, model::ABM{<:ContinuousSpace}, dt::Real)
```

Propagate the agent forwards one step according to its velocity, *after* updating the agent's velocity (if configured using `update_vel!`, see [`ContinuousSpace`](@ref)).

For this continuous space version of `move_agent!`, the "time evolution" is a trivial Euler scheme with `dt` the step size, i.e. the agent position is updated as `agent.pos += agent.vel * dt`.

Unlike `move_agent!(agent, [pos,] model)`, this function respects the space size. For non-periodic spaces, agents will walk up to, but not reach, the space extent. For periodic spaces movement properly wraps around the extent.
