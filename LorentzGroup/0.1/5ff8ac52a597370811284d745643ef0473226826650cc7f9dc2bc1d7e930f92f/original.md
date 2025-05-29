```
GenMatrix{T} <: Generator{T}
```

A 4×4 `StaticMatrix` wrapper type for elements of the 4-dimensional vector representation of the Lorentz algebra.  This type is analogous to [`LorMatrix`](@ref) and should be considered a "fallback" for cases where elements of the algebra can't be represented more succinctly as with e.g. [`Gen`](@ref) or [`ScaledGen`](@ref).

**WARN** Constructors for this type check the dimensionality of arguments but do *NOT* check that the argument is a valid element of the representation.
