```
struct CurvatureTerm{V,M} <: LevelSetTerm
```

Level-set curvature term representing `bκ|∇ϕ|`, where `κ = ∇ ⋅ (∇ϕ/|∇ϕ|)` is the curvature.
