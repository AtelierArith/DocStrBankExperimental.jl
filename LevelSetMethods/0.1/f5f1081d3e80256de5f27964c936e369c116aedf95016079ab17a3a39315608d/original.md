```
integrate!(ls::LevelSetEquation,tf,Δt=Inf)
```

Integrate the [`LevelSetEquation`](@ref) `ls` up to time `tf`, mutating the `levelset` and `current_time` of the object `ls` in the process.

An optional parameter `Δt` can be passed to specify a maximum time-step allowed for the integration. Note that the internal time-steps taken to evolve the level-set up to `tf` may be smaller than `Δt` due to stability reasons related to the `terms` and `integrator` employed.
