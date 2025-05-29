```
StopWhenSwarmVelocityLess <: StoppingCriterion
```

Stopping criterion for [`particle_swarm`](@ref), when the velocity of the swarm is less than a threshold.

# Fields

  * `threshold`:      the threshold
  * `at_iteration`:   store the iteration the stopping criterion was (last) fulfilled
  * `reason`:         store the reason why the stopping criterion was fulfilled, see [`get_reason`](@ref)
  * `velocity_norms`: interim vector to store the norms of the velocities before computing its norm

# Constructor

```
StopWhenSwarmVelocityLess(tolerance::Float64)
```

initialize the stopping criterion to a certain `tolerance`.
