```
timeseries!([p::AbstractParticle,] bd::Billiard, t; dt, warning)
```

Evolve the given particle `p` inside the billiard `bd` for the condition `t` and return the x, y, vx, vy timeseries and the time vector. If `t` is of type `AbstractFloat`, then evolve for as much time as `t`. If however `t` is of type `Int`, evolve for as many collisions as `t`. Otherwise, `t` can be any function, that takes as an input `t(n, τ, i, p)` and returns `true` when the evolution should terminate. Here `n` is the amount of obstacles collided with so far, `τ` the amount time evolved so far, `i` the obstacle just collided with and `p` the particle (so you can access e.g. `p.pos`).

This function mutates the particle, use `timeseries` otherwise. If a particle is not given, a random one is picked through [`randominside`](@ref).

The keyword argument `dt` is the time step used for interpolating the time series in between collisions. `dt` is capped by the collision time, as the interpolation *always* stops at collisions. For straight propagation `dt = Inf`, while for magnetic `dt = 0.01`.

For pinned magnetic particles, `timeseries!` issues a warning and returns the trajectory of the particle. If `t` is integer, the trajectory is evolved for one full circle only.

Internally uses [`DynamicalBilliards.extrapolate`](@ref).

### Ray-splitting billiards

```
timeseries!(p, bd, t, raysplitters; ...)
```

To implement ray-splitting, the `timeseries!` function is supplemented with a fourth argument, `raysplitters` which is a tuple of [`RaySplitter`](@ref) instances. Notice that `timeseries` **always mutates the billiard** if ray-splitting is used! For more information and instructions on using ray-splitting please visit the official documentation.
