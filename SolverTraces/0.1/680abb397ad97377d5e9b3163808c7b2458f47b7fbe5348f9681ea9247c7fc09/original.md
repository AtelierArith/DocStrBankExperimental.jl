```
TraceColumn
```

Base type for all columns that can appear in a [`SolverTrace`](@ref). Each subtype is expected to have a property named `fmt` containing a formatting string, and to be callable with the current step number as argument, returning the necessary values to render the formatting string, alternatively overload `Format.format(c::C, i::Integer) where {C<:TraceColumn}`.
