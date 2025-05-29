```
effects(design::AbstractDict, model::RegressionModel;
        eff_col=nothing, err_col=:err, typical=mean,
        lower_col=:lower, upper_col=:upper, invlink=identity,
        vcov=StatsBase.vcov, level=nothing)
```

Compute the `effects` as specified by the `design`.

This is a convenience wrapper for [`effects!`](@ref). Instead of specifying a reference grid, a dictionary containing the levels/values of each predictor is specified. This is then expanded into a reference grid representing a fully-crossed design. Additionally, two extra columns are created representing the lower and upper edges of the confidence interval. The default `level=nothing` corresponds to [resp-err, resp+err], while `level=0.95` corresponds to the 95% confidence interval.

See also [`AutoInvLink`](@ref).
