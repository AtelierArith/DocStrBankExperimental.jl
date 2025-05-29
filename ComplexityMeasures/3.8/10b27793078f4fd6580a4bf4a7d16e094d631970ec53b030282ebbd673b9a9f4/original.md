```
codify(o::OutcomeSpace, x::Vector) → s::Vector{Int}
```

Codify `x` according to the outcome space `o`.

## Description

The reason this function exists is that we don't always want to [`encode`](@ref) the entire input `x` at once. Sometimes, it is desirable to first apply some transformation to `x` first, then apply [`Encoding`](@ref)s in a point-wise manner in the transformed space. (the [`OutcomeSpace`](@ref) dictates this transformation). This is useful for encoding timeseries data.

The length of the returned `s` depends on the [`OutcomeSpace`](@ref). Some outcome spaces preserve the input data length (e.g. [`UniqueElements`](@ref)), while some outcome spaces (e.g. [`OrdinalPatterns`](@ref)) do e.g. delay embeddings before encoding, so that `length(s) < length(x)`.
