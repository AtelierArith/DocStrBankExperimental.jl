```
prepare_heterotopic_multi_output_data(
    x::AbstractVector, y::AbstractVector{<:Real}, output_indices::AbstractVector{Int},
)
```

Utility functionality to convert a collection of inputs `x`, observations `y`, and `output_indices` into a format suitable for use with multi-output kernels. Handles the situation in which only one (or a subset) of outputs are observed at each feature. Ensures that all arguments are compatible with one another, and returns a vector of inputs and a vector of outputs.

`y[n]` should be the observed value associated with output `output_indices[n]` at feature `x[n]`.

```jldoctest
julia> x = [1.0, 2.0, 3.0];

julia> y = [-1.0, 0.0, 1.0];

julia> output_indices = [3, 2, 1];

julia> inputs, outputs = prepare_heterotopic_multi_output_data(x, y, output_indices);

julia> inputs
3-element Vector{Tuple{Float64, Int64}}:
 (1.0, 3)
 (2.0, 2)
 (3.0, 1)

julia> outputs
3-element Vector{Float64}:
 -1.0
  0.0
  1.0
```

See also [`prepare_isotopic_multi_output_data`](@ref).
