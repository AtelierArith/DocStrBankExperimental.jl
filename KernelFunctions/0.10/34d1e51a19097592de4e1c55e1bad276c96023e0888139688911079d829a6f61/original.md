```
MOInput(x::AbstractVector, out_dim::Integer)
```

A data type to accommodate modelling multi-dimensional output data. `MOInput(x, out_dim)` has length `length(x) * out_dim`.

```jldoctest
julia> x = [1, 2, 3];

julia> MOInput(x, 2)
6-element KernelFunctions.MOInputIsotopicByOutputs{Int64, Vector{Int64}, Int64}:
 (1, 1)
 (2, 1)
 (3, 1)
 (1, 2)
 (2, 2)
 (3, 2)
```

As shown above, an `MOInput` represents a vector of tuples. The first `length(x)` elements represent the inputs for the first output, the second `length(x)` elements represent the inputs for the second output, etc. See [Inputs for Multiple Outputs](@ref) in the docs for more info.

`MOInput` will be deprecated in version 0.11 in favour of `MOInputIsotopicByOutputs`, and removed in version 0.12.
