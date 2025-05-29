```
updateone!(b::Booster, data, ℓ′, ℓ″; kw...)
```

Run one of gradient boosting with a loss function `ℓ`.  `ℓ′` and `ℓ″` are the first and second *scalar* derivatives of the loss function.  For example

```julia
ℓ(ŷ, y) = (ŷ - y)^2
ℓ′(ŷ, y) = 2(ŷ - y)
ℓ″(ŷ, y) = 2
```

where the derivatives are with respect to the first argument (the prediction).

Other arguments are the same as they would be provided to other methods of `updateone!`.
