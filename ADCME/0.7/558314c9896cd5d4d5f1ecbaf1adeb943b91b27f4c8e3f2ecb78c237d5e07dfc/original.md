```
dropout(x::Union{PyObject, Real, Array{<:Real}}, 
rate::Union{Real, PyObject}, training::Union{PyObject,Bool} = true; kwargs...)
```

Randomly drops out entries in `x` with a rate of `rate`. 
