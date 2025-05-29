```
particle_swarm!(M, f, swarm; kwargs...)
particle_swarm!(M, mco::AbstractManifoldCostObjective, swarm; kwargs..)
```

perform the particle swarm optimization algorithm (PSO), starting with the initial `swarm` which is then modified in place.

# Input

  * `M`:     a manifold $\mathcal M$
  * `f`:     a cost function $f:\mathcal M→ℝ$ to minimize
  * `swarm`: (`[rand(M) for _ in 1:swarm_size]`) an initial swarm of points.

Instead of a cost function `f` you can also provide an [`AbstractManifoldCostObjective`](@ref) `mco`.

For more details and optional arguments, see [`particle_swarm`](@ref).
