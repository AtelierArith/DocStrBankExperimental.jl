```
struct Dimensions{N,T<:Tuple} <: AbstractDimensions{N, N}
    to::T
end
```

A structure that describes the Hilbert [`Space`](@ref) of each subsystems.
