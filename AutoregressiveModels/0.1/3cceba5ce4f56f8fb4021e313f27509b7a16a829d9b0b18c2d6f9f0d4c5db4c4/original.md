```
simulate(εs::AbstractArray, var::VARProcess, Y0=nothing; nlag::Integer=arorder(var))
```

Same as [`simulate!`](@ref), but makes a copy of `εs` for results and hence does not overwrite `εs`.
