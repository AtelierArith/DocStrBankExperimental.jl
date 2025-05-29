coerce!(X, ...)

Same as [`ScientificTypes.coerce`](@ref) except it does the modification in place provided `X` supports in-place modification (eg, DataFrames). An error is thrown otherwise. The arguments are the same as `coerce`.
