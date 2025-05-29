```
Δsize!(f::F, ins::AbstractVector, outs::AbstractVector; kwargs...)
```

Apply the changes to `f` so that input neurons in `ins` and output neurons in `outs` are selected and/or inserted.

Argument `outs` is a vector of indices to select/insert while `ins` has one vector of indices per input vertex.

Shall be implemented for any type `F` which holds parameters for which the shape shall be modified by NaiveNASlib.

Tip: the function [`parselect`](@ref) can be used to change parameter arrays according to `ins` and `outs`.

Tip: `kwargs` can be passed using [`WithKwargs`](@ref).
