```
SteepestDirectionUpdateRule <: DirectionUpdateRule
```

The simplest rule to update is to have no influence of the last direction and hence return an update $β = 0$ for all [`ConjugateGradientDescentState`](@ref)`cgds`

See also [`conjugate_gradient_descent`](@ref)
