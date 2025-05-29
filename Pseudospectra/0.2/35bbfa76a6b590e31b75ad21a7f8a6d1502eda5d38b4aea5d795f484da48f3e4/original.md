```
new_matrix(A, opts::Dict{Symbol,Any}=()) -> ps_data
```

process a linear operator object into the auxiliary data structure used by Pseudospectra.

There must be methods with `A` for `eltype`, `size`, and `mul!`. It is up to the user to make sure that `mul!` is consistent with any options passed to the iterative solver (see documentation for [`xeigs`](@ref)).
