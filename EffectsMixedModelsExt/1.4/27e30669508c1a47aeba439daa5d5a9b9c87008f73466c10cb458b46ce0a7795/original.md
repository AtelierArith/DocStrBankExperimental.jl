```
effects(design::AbstractDict, model::MixedModel, boot::MixedModelBootstrap;
        eff_col=nothing, err_col=:err, typical=mean,
        lower_col=:lower, upper_col=:upper, invlink=identity,
        level=nothing)
```

Use the results of a bootstrap to compute empirical error estimates (instead of using the variance-covariance matrix).

!!! warning
    This method is experimental and may change in its defaults or disappear entirely in a future release!

