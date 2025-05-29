```
BoxCoxTransformation <: PowerTransformation
```

# Fields

  * `λ`: The transformation parameter
  * `y`: The original response, normalized by its geometric mean
  * `X`: A model matrix for the conditional distribution or `Nothing` for the unconditional distribution
  * `atol`: Tolerance for comparing λ to zero. Default is 1e-8

!!! note
    All fields are considered internal and implementation details and may change at any time without being considered breaking.


# Tips

  * To extract the λ parameter, use `params`.
  * The transformation is callable, meaning that you can do

```@example
bc = fit(BoxCoxTransformation, y)
y_transformed = bc.(y)
```

  * You can reduce the size of a BoxCoxTransformation in memory by using `empty!`, but certain diagnostics (e.g. plotting and computation of the loglikelihood will no longer be available).

See also [`boxcoxplot`](@ref), [`params`](@ref), [`boxcox`](@ref).
