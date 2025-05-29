```
YeoJohnsonTransformation <: PowerTransformation
```

# Fields

  * `λ`: The transformation parameter
  * `y`: The original response
  * `X`: A model matrix for the conditional distribution or `Nothing` for the unconditional distribution
  * `atol`: Tolerance for comparing λ to zero or two. Default is 1e-8

!!! note
    All fields are considered internal and implementation details and may change at any time without being considered breaking.


# Tips

  * To extract the λ parameter, use `params`.
  * The transformation is callable, meaning that you can do

```@example
yj = fit(YeoJohnsonTransformation, y)
y_transformed = yj.(y)
```

  * You can reduce the size of a YeoJohnsonTransformation in memory by using `empty!`, but certain diagnostics (e.g. plotting and computation of the loglikelihood will no longer be available).
