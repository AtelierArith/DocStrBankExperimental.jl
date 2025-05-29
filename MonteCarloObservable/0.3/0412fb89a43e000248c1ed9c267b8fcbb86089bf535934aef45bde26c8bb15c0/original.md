```
saveobs(obs::Observable{T}[, filename::AbstractString, entryname::AbstractString])
```

Saves complete representation of the observable to JLD file.

Default filename is "Observables.jld" and default entryname is `name(obs)`.

See also [`loadobs`](@ref).
