```
project(M::ProbabilitySimplex, p, Y)
```

Project `Y` from the embedding onto the tangent space at `p` on the [`ProbabilitySimplex`](@ref) `M`. The formula reads

``math \operatorname{proj}_{Δ^n}(p,Y) = Y - \bar{Y}` where $\bar{Y}$ denotes mean of $Y$.
