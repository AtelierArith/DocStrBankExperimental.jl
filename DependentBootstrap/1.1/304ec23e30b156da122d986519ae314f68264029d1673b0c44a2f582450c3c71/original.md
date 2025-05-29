```
dbootinds(data::T ; bi::BootInput)::Vector{Vector{Int}}
dbootinds(data::T ; kwargs...)::Vector{Vector{Int}}
```

Each inner vector of the returned Vector{Vector{Int}} provides indices that, when used to index the original dataset, will provide a single resampled dataset.

A keyword method that calls the keyword constructor for BootInput is also provided. Please use ?BootInput at the REPL for more detail on feasible keywords.

Please use dbootinds_one if you only want to obtain a single Vector{Int} resampling index.
