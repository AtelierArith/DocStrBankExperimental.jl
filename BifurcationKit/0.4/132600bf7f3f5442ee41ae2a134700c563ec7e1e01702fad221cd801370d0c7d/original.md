```julia
mutable struct BorderedArray{vectype1, vectype2}
```

This defines an array (although not `<: AbstractArray`) to hold two arrays or an array and a scalar.  This is useful when one wants to add constraints (phase, ...) to a functional for example.  It is used throughout the package for the Pseudo Arc Length Continuation (PALC), for the continuation of Fold / Hopf points, for periodic orbits...  It is also used to define periodic orbits as (orbit, period). As such, it is a convenient alternative to `cat`, `vcat` and friends.  We chose not to make it a subtype of AbstractArray as we wish to apply the current package to general "arrays", see [Requested methods for Custom State](@ref).  Finally, it proves useful for the GPU where the operation `x[end]` can be slow.
