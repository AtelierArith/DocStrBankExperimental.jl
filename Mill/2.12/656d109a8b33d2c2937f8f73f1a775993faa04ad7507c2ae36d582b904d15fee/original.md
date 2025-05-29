```
MaybeHotMatrix{T, V} <: AbstractMatrix{U}
```

A matrix-like structure for representing one-hot encoded variables. Like `Flux.OneHotMatrix` but supports `missing` values.

Construct with the [`maybehotbatch`](@ref) function.

See also: [`MaybeHotVector`](@ref), [`maybehot`](@ref).
