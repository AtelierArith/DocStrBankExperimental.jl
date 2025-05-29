```
AbstractDimArray <: AbstractArray
```

Abstract supertype for all "dim" arrays.

These arrays return a `Tuple` of [`Dimension`](@ref) from a [`dims`](@ref) method, and can be rebuilt using [`rebuild`](@ref).

`parent` must return the source array.

They should have [`metadata`](@ref), [`name`](@ref) and [`refdims`](@ref) methods, although these are optional.

A [`rebuild`](@ref) method for `AbstractDimArray` must accept `data`, `dims`, `refdims`, `name`, `metadata` arguments.

Indexing `AbstractDimArray` with non-range `AbstractArray` has undefined effects on the `Dimension` index. Use forward-ordered arrays only"
