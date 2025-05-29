```
get_var(
    expname ::String,
    snap    ::Union{<:Integer, AbstractVector{<:Integer}},
    expdir  ::String,
    variable::String,
    args...
    ;
    kwargs...
)
```

Load a `variable` from one or multiple snapshots of a Bifrost experiment with experiment directory `expdir` and experiment name `expname`.
