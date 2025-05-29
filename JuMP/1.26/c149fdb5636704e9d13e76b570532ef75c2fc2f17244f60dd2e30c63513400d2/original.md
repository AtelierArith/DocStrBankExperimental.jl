```
delete(model::GenericModel, con_refs::Vector{<:ConstraintRef})
```

Delete the constraints associated with `con_refs` from the model `model`.

Solvers may implement specialized methods for deleting multiple constraints of the same concrete type. These methods may be more efficient than repeatedly calling the single constraint `delete` method.

See also: [`unregister`](@ref)

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:3]);

julia> @constraint(model, c, 2 * x .<= 1)
3-element Vector{ConstraintRef{Model, MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64}, MathOptInterface.LessThan{Float64}}, ScalarShape}}:
 c : 2 x[1] ≤ 1
 c : 2 x[2] ≤ 1
 c : 2 x[3] ≤ 1

julia> delete(model, c)

julia> unregister(model, :c)

julia> print(model)
Feasibility
Subject to

julia> model[:c]
ERROR: KeyError: key :c not found
Stacktrace:
[...]
```
