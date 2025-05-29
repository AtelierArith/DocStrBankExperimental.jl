```julia
fixed_stepsize_warmup_stages(
;
    M,
    middle_steps,
    doubling_stages
)

```

A sequence of warmup stages for fixed stepsize, only tuning covariance: first with `middle_steps` steps, then repeat with twice the steps `doubling_stages` times

Very similar to [`default_warmup_stages`](@ref), but omits the warmup stages with just stepsize tuning.
