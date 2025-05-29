```
struct GeneralDimensions{N,T1<:Tuple,T2<:Tuple} <: AbstractDimensions{N}
    to::T1
    from::T2
end
```

A structure that describes the left-hand side (`to`) and right-hand side (`from`) Hilbert [`Space`](@ref) of an [`Operator`](@ref).
