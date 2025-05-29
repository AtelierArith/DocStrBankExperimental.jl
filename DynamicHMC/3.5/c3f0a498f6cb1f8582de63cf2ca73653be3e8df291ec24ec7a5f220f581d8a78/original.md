```julia
default_warmup_stages(
;
    stepsize_search,
    M,
    stepsize_adaptation,
    init_steps,
    middle_steps,
    doubling_stages,
    terminating_steps
)

```

A sequence of warmup stages:

1. select an initial stepsize using `stepsize_search` (default: based on a heuristic),
2. tuning stepsize with `init_steps` steps
3. tuning stepsize and covariance: first with `middle_steps` steps, then repeat with twice the steps `doubling_stages` times
4. tuning stepsize with `terminating_steps` steps.

`M` (`Diagonal`, the default or `Symmetric`) determines the type of the metric adapted from the sample.

This is the suggested tuner of most applications.

Use `nothing` for `stepsize_adaptation` to skip the corresponding step.
