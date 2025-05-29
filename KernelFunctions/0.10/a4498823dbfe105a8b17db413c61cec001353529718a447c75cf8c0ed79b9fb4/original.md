```
prepare_isotopic_multi_output_data(x::AbstractVector, y::RowVecs)
```

Utility functionality to convert a collection of `N = length(x)` inputs `x` and output vectors `y` (efficiently represented by a `RowVecs`) into a format suitable for use with multi-output kernels.

`y[n]` is the vector-valued output corresponding to the input `x[n]`. Consequently, it is necessary that `length(x) == length(y)`.

For example, if outputs are initial stored in an `N × num_outputs` matrix:

```jldoctest
julia> x = [1.0, 2.0, 3.0];

julia> Y = [1.1 1.2; 2.1 2.2; 3.1 3.2]
3×2 Matrix{Float64}:
 1.1  1.2
 2.1  2.2
 3.1  3.2

julia> inputs, outputs = prepare_isotopic_multi_output_data(x, RowVecs(Y));

julia> inputs
6-element KernelFunctions.MOInputIsotopicByOutputs{Float64, Vector{Float64}, Int64}:
 (1.0, 1)
 (2.0, 1)
 (3.0, 1)
 (1.0, 2)
 (2.0, 2)
 (3.0, 2)

julia> outputs
6-element Vector{Float64}:
 1.1
 2.1
 3.1
 1.2
 2.2
 3.2
```

See also [`prepare_heterotopic_multi_output_data`](@ref).
