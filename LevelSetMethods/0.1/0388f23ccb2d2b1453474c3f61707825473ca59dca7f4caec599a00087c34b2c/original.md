```
struct NormalMotionTerm{V,M} <: LevelSetTerm
```

Level-set advection term representing  `v |∇ϕ|`. This `LevelSetTerm` should be used for internally generated velocity fields; for externally generated velocities you may use `AdvectionTerm` instead.
