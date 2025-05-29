```
init!(tracker::Tracker, x₁, t₁, t₀)
```

Setup `tracker` to track `x₁` from `t₁` to `t₀`.

```
init!(tracker::Tracker, t₀)
```

Setup `tracker` to continue tracking the current solution to `t₀`. This keeps the current state.
