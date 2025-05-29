```
restorereplicates(f, m::MixedModel{T})
restorereplicates(f, m::MixedModel{T}, ftype::Type{<:AbstractFloat})
restorereplicates(f, m::MixedModel{T}, ctype::Type{<:MixedModelFitCollection{S}})
```

Restore replicates from `f`, using `m` to create the desired subtype of [`MixedModelFitCollection`](@ref).

`f` can be any entity supported by `Arrow.Table`. `m` does not have to be fitted, but it must have been constructed with the same structure as the source of the saved replicates.

The two-argument method constructs a [`MixedModelBootstrap`](@ref) with the same eltype as `m`. If an eltype is specified as the third argument, then a `MixedModelBootstrap` is returned. If a subtype of `MixedModelFitCollection` is specified as the third argument, then that is the return type.

See also [`savereplicates`](@ref), [`restoreoptsum!`](@ref).
