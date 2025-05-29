```
track!(tracker::Tracker, x, t₁ = 1.0, t₀ = 0.0; debug::Bool = false)
```

The same as [`track`](@ref) but only returns the final [`TrackerCode`](@ref).

```
track!(tracker::Tracker, t₀; debug::Bool = false)
```

Track with `tracker` the current solution to `t₀`. This keeps the current state.
