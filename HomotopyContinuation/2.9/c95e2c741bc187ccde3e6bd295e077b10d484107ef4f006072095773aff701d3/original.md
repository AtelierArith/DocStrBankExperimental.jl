```
 track(tracker::Tracker, x::AbstractVector, t₁ = 1.0, t₀ = 0.0; debug::Bool = false)
```

Track the given solution `x` at `t₁` using `tracker` to a solution at `t₀`.

```
track(tracker::Tracker, r::TrackerResult, t₁ = 1.0, t₀ = 0.0; debug::Bool = false)
```

Track the solution of the result `r` from `t₁` to `t₀`.
