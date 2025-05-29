```
correlation_length(above::InfiniteMPS; kwargs...)
```

Compute the correlation length of a given InfiniteMPS based on the next-to-leading eigenvalue of the transfer matrix. The `kwargs` are passed to [`transfer_spectrum`](@ref), and can for example be used to target the correlation length in a specific sector. 
