```
L₂(x̄)
```

Returns a discretized second-order differential operator of `length(x̄)` by `length(x̄) + 2` matrix using central difference under no boundary condition.

The first and last columns are applied to the ghost nodes just before `x̄[1]` and `x̄[end]` respectively.

# Examples

```jldoctest; setup = :(using SimpleDifferentialOperators)
julia> x̄ = 0:5
0:5 

julia> Array(L₂(x̄))
4×6 Array{Float64,2}:
 1.0  -2.0   1.0   0.0   0.0  0.0
 0.0   1.0  -2.0   1.0   0.0  0.0
 0.0   0.0   1.0  -2.0   1.0  0.0
 0.0   0.0   0.0   1.0  -2.0  1.0
```
