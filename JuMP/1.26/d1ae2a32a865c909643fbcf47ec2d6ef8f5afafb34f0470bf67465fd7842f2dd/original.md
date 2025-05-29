```
triangle_vec(matrix::Matrix)
```

Return the upper triangle of a matrix concatenated into a vector in the order required by JuMP and MathOptInterface for `Triangle` sets.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, X[1:3, 1:3], Symmetric);

julia> @variable(model, t)
t

julia> @constraint(model, [t; triangle_vec(X)] in MOI.RootDetConeTriangle(3))
[t, X[1,1], X[1,2], X[2,2], X[1,3], X[2,3], X[3,3]] ∈ MathOptInterface.RootDetConeTriangle(3)
```
