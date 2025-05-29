```
MaybeHotVector{T, U} <: AbstractVector{U}
```

A vector-like structure for representing one-hot encoded variables. Like `Flux.OneHotVector` but supports `missing` values.

Construct with the [`maybehot`](@ref) function.

See also: [`MaybeHotMatrix`](@ref), [`maybehotbatch`](@ref).
