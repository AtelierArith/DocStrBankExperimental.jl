```
source_term_bottom_friction(u, x, t, equations::ShallowWaterExnerEquations1D)
```

[ShallowWaterExnerEquations1D](@ref)における底面摩擦を考慮したソース項。実際の摩擦法則は`equations.friction`の摩擦モデルを通じて決定されます。
