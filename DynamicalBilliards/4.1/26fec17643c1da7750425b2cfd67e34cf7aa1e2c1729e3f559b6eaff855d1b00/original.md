```
particlebeam(x0, y0, φ, N, dx, ω = nothing, T = eltype(x0)) → ps
```

Make `N` particles, all with direction `φ`, starting at `x0, y0`. The particles don't all have the same position, but are instead spread by up to `dx` in the direction normal to `φ`.

The particle element type is `T`.
