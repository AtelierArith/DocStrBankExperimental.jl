```
relax_with_penalty!(
    model::GenericModel{T},
    [penalties::Dict{ConstraintRef,T}];
    [default::Union{Nothing,Real} = nothing,]
) where {T}
```

Destructively modify the model in-place to create a penalized relaxation of the constraints.

!!! warning
    This is a destructive routine that modifies the model in-place. If you don't want to modify the original model, use [`copy_model`](@ref) to create a copy before calling [`relax_with_penalty!`](@ref).


## Reformulation

See [`MOI.Utilities.ScalarPenaltyRelaxation`](@ref) for details of the reformulation.

For each constraint `ci`, the penalty passed to [`MOI.Utilities.ScalarPenaltyRelaxation`](@ref) is `get(penalties, ci, default)`. If the value is `nothing`, because `ci` does not exist in `penalties` and `default = nothing`, then the constraint is skipped.

## Return value

This function returns a `Dict{ConstraintRef,AffExpr}` that maps each constraint index to the corresponding `y + z` as an [`AffExpr`](@ref). In an optimal solution, query the value of these functions to compute the violation of each constraint.

## Relax a subset of constraints

To relax a subset of constraints, pass a `penalties` dictionary and set `default = nothing`.

## Example

```jldoctest
julia> function new_model()
           model = Model()
           @variable(model, x)
           @objective(model, Max, 2x + 1)
           @constraint(model, c1, 2x - 1 <= -2)
           @constraint(model, c2, 3x >= 0)
           return model
       end
new_model (generic function with 1 method)

julia> model_1 = new_model();

julia> penalty_map = relax_with_penalty!(model_1; default = 2.0);

julia> penalty_map[model_1[:c1]]
_[3]

julia> penalty_map[model_1[:c2]]
_[2]

julia> print(model_1)
Max 2 x - 2 _[2] - 2 _[3] + 1
Subject to
 c2 : 3 x + _[2] ≥ 0
 c1 : 2 x - _[3] ≤ -1
 _[2] ≥ 0
 _[3] ≥ 0

julia> model_2 = new_model();

julia> relax_with_penalty!(model_2, Dict(model_2[:c2] => 3.0))
Dict{ConstraintRef{Model, MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64}, MathOptInterface.GreaterThan{Float64}}, ScalarShape}, AffExpr} with 1 entry:
  c2 : 3 x + _[2] ≥ 0 => _[2]

julia> print(model_2)
Max 2 x - 3 _[2] + 1
Subject to
 c2 : 3 x + _[2] ≥ 0
 c1 : 2 x ≤ -1
 _[2] ≥ 0
```
