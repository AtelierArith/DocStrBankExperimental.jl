```
struct ReinitializationTerm <: LevelSetTerm
```

Level-set term representing  `sign(ϕ) (|∇ϕ| - 1)`. This `LevelSetTerm` should be used for reinitializing the level set into a signed distance function: for a sufficiently large number of time steps this term allows one to solve the Eikonal equation |∇ϕ| = 1.
