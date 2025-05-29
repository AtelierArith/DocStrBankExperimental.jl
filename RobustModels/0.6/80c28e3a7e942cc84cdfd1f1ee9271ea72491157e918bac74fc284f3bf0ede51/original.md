```
refit!(m::QuantileRegression,
      [y::FPVector ;
       verbose::Bool=false,
       quantile::Union{Nothing,
       AbstractFloat}=nothing,
      ]
)
```

Refit the `QuantileRegression` model with the new values for the response, weights and quantile. This function assumes that `m` was correctly initialized.
