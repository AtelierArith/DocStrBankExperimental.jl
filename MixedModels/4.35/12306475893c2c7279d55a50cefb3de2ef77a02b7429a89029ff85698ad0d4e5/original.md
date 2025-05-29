```
confint(pr::MixedModelProfile; level::Real=0.95)
```

Compute profile confidence intervals for (fixed effects) coefficients, with confidence level `level` (by default 95%).

!!! note
    The API guarantee is for a Tables.jl compatible table. The exact return type is an implementation detail and may change in a future minor release without being considered breaking.

