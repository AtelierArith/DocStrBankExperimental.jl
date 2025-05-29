```
LorMatrix{T} <: Lorentz{T}
```

A 4×4 `StaticMatrix` wrapper type for elements of the vector representation of the Lorentz group. This type should be considered a "fallback" for cases where group elements can't be represented more succinctly in types such as [`Exp`](@ref).

**WARN** Constructors for this type check the dimensionality of arguments but do *NOT* check that the argument is a valid element of the representation.
