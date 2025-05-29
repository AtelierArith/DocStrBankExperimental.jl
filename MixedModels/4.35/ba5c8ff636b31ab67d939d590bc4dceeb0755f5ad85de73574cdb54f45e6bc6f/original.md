```
 MixedModelProfile{T<:AbstractFloat}
```

Type representing a likelihood profile of a [`LinearMixedModel`](@ref), including associated interpolation splines.

The function [`profile`](@ref) is used for computing profiles, while [`confint`](@ref) provides a useful method for constructing confidence intervals from a `MixedModelProfile`.

!!! note
    The exact fields and their representation are considered implementation details and are **not** part of the public API.

