```
struct CurvatureTerm{V,M} <: LevelSetTerm
```

レベルセット曲率項は `bκ|∇ϕ|` を表し、ここで `κ = ∇ ⋅ (∇ϕ/|∇ϕ|)` は曲率です。
