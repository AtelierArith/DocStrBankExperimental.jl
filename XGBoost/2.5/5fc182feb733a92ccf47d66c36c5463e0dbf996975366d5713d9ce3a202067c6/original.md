```
update!(b::Booster, data; num_round=1, kw...)
update!(b::Booster, data, ℓ′, ℓ″; kw...)
```

Run `num_round` rounds of gradient boosting on [`Booster`](@ref) `b`.

The first and second derivatives of the loss function (`ℓ′` and `ℓ″` respectively) can be provided for custom loss.
