```
PencilArrayCollection
```

`UnionAll` type describing a collection of [`PencilArray`](@ref)s.

Such a collection can be a tuple or an array of `PencilArray`s.

Collections are **by assumption** homogeneous: each array has the same properties, and in particular, is associated to the same [`Pencil`](@ref) configuration.

For convenience, certain operations defined for `PencilArray` are also defined for `PencilArrayCollection`, and return the same value as for a single `PencilArray`. Some examples are [`pencil`](@ref), [`range_local`](@ref) and [`get_comm`](@ref).

Also note that functions from `Base`, such as `size`, `ndims` and `eltype`, are **not** overloaded for `PencilArrayCollection`, since they already have a definition for tuples and arrays (and redefining them would be type piracy...).
