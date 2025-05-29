```
find_symmetries(pge::PeriodicGraphEmbedding3D, vtypes=nothing, check_symmetry=check_valid_symmetry; tolerance::Union{Nothing,Cdouble}=nothing)
```

Return a [`SymmetryGroup3D`](@ref) object storing the list of symmetry operations on the graph embedding, found using spglib. Use [`retrieve_symmetries`](@ref) to simply extract the symmetries already specified in the [`Cell`](@ref) of the graph embedding.

If `vtypes !== nothing`, ensure that two vertices `x` and `y` cannot be symmetry-related if `vtypes[x] != vtypes[y]`.

`check_symmetry` must be a function that takes the same four arguments `pge`, `t`, `r` and `vtypes` as `check_valid_symmetry` and return either `(vmap, offsets)` or `nothing` if the input is not a valid symmetry. It can be used to specify additional constraints that cannot be carried by `vtypes` alone.

An explicit tolerance can be set. Otherwise, the default is a loose tolerance if the positions are floating points, or a stringent tolerance if they are rationals.
