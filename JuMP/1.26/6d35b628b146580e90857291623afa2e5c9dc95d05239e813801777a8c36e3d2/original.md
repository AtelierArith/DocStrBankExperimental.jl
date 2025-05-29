```
SOS2(weights = Real[])
```

The SOS2 (Special Ordered Set of Type 2) set constrains a vector `x` to the set where at most two variables can take a non-zero value, and all other elements are zero. In addition, the two non-zero values must be consecutive given the ordering of the `x` vector induced by `weights`.

The `weights` vector, if specified, induces an ordering of the variables; as such, it must contain unique values. The `weights` vector must have the same number of elements as the vector `x`, and the element `weights[i]` corresponds to element `x[i]`. If not provided, the `weights` vector defaults to `weights[i] = i`.

This is a shortcut for the [`MOI.SOS2`](@ref) set.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:3] in SOS2([4.1, 3.2, 5.0]))
3-element Vector{VariableRef}:
 x[1]
 x[2]
 x[3]

julia> print(model)
Feasibility
Subject to
 [x[1], x[2], x[3]] ∈ MathOptInterface.SOS2{Float64}([4.1, 3.2, 5.0])
```
