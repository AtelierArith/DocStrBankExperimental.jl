```
source_term_bottom_friction(u, x, t, equations::ShallowWaterExnerEquations1D)
```

Source term that accounts for the bottom friction in the [ShallowWaterExnerEquations1D](@ref). The actual friction law is determined through the friction model in `equations.friction`.
