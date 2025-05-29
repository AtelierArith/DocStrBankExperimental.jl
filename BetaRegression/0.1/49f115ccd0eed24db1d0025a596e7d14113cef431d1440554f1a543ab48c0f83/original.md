```
BetaRegressionModel(X, y, link=LogitLink(), precisionlink=IdentityLink();
                    weights=nothing, offset=nothing)
```

Construct a `BetaRegressionModel` object with the given model matrix `X`, response `y`, mean link function `link`, precision link function `precisionlink`, and optionally `weights` and `offset`. Note that the returned object is not fit until `fit!` is called on it.

!!! warning
    Support for user-provided weights is currently incomplete; passing a value other than `nothing` or an empty array for `weights` will result in an error for now.

