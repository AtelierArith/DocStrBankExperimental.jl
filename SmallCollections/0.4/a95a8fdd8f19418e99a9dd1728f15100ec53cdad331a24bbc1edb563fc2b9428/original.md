```
SmallCollections
```

This packages provides several mutable and immutable collections that can hold a fixed or limited (small) number of elements and are much more efficient than `Set` and `Vector`, for example. This applies in particular to the immutable variants because they don't allocate if `isbitstype` holds for the element type. At present, `FixedVector`, `SmallVector`, `SmallDict` and `SmallSet` and their mutable counterparts are defined as well as `PackedVector` and `SmallBitSet`.

The submodule [`Combinatorics`](@ref) contains functions related to enumerative combinatorics.

If the package `BangBang.jl` is loaded, then many functions defined by this package are also available in `!!`-form. For example, `setindex!!` with a `SmallVector` as first argument calls [`setindex`](@ref).

Bounds checking can be skipped for the functions defined in this package by using the `@inbounds` macro.

See [`AbstractFixedVector`](@ref), [`AbstractSmallDict`](@ref), [`AbstractSmallSet`](@ref), [`AbstractSmallVector`](@ref), [`PackedVector`](@ref), [`SmallBitSet`](@ref), [`Combinatorics`](@ref), `Base.@inbounds`, `Base.isbitstype`, [Section "BangBang support"](@ref sec-bangbang).
