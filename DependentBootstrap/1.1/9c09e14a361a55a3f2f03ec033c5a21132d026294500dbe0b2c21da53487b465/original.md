```
dbootdata(data::T , bi::BootInput)::Vector{T}
dbootdata(data::T ; kwargs...)::Vector{T}
```

Get the resampled datasets of the input data using the dependent bootstrap methodology defined in BootInput.

A keyword method that calls the keyword constructor for BootInput is also provided. Please use ?BootInput at the REPL for more detail on feasible keywords.

Note, this function should always have output type Vector{T}.
