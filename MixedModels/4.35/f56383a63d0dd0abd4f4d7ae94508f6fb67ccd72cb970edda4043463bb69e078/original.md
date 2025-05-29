```
fit!(m::LinearMixedModel; progress::Bool=true, REML::Bool=m.optsum.REML,
                          σ::Union{Real, Nothing}=m.optsum.sigma,
                          thin::Int=typemax(Int),
                          fitlog::Bool=true)
```

Optimize the objective of a `LinearMixedModel`.  When `progress` is `true` a `ProgressMeter.ProgressUnknown` display is shown during the optimization of the objective, if the optimization takes more than one second or so.

The `thin` argument is ignored: it had no impact on the final model fit and the logic around thinning the `fitlog` was needlessly complicated for a trivial performance gain.
