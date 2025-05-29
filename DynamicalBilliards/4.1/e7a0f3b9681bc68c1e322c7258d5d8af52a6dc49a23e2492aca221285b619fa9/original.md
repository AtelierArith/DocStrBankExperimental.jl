```
evolve!([p::AbstractParticle,] bd::Billiard, t)
```

Evolve the given particle `p` inside the billiard `bd`. If `t` is of type `AbstractFloat`, evolve for as much time as `t`. If however `t` is of type `Int`, evolve for as many collisions as `t`. Return the states of the particle between collisions.

This function mutates the particle, use `evolve` otherwise. If a particle is not given, a random one is picked through [`randominside`](@ref).

### Return

  * `ct::Vector{T}` : Collision times.
  * `poss::Vector{SVector{2,T}}` : Positions at the collisions.
  * `vels::Vector{SVector{2,T}})` : Velocities exactly after the collisions.
  * `ω`, either `T` or `Vector{T}` : Angular velocity/ies (returned only for magnetic particles).

The time `ct[i+1]` is the time necessary to reach state `poss[i+1], vels[i+1]` starting from the state `poss[i], vels[i]`. That is why `ct[1]` is always 0 since `poss[1], vels[1]` are the initial conditions. The angular velocity `ω[i]` is the one the particle has while propagating from state `poss[i], vels[i]` to `i+1`.

Notice that at any point, the velocity vector `vels[i]` is the one obdained *after* the specular reflection of the `i-1`th collision.

### Ray-splitting billiards

```
evolve!(p, bd, t, raysplitters)
```

To implement ray-splitting, the `evolve!` function is supplemented with a fourth argument, `raysplitters` which is a tuple of [`RaySplitter`](@ref) instances. Notice that `evolve` **always mutates the billiard** if ray-splitting is used! For more information and instructions on using ray-splitting please visit the official documentation.
