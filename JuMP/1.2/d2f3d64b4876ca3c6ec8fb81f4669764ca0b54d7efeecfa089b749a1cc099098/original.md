```
primal_feasibility_report(
    model::Model,
    point::AbstractDict{VariableRef,Float64} = _last_primal_solution(model),
    atol::Float64 = 0.0,
    skip_missing::Bool = false,
)::Dict{Any,Float64}
```

Given a dictionary `point`, which maps variables to primal values, return a dictionary whose keys are the constraints with an infeasibility greater than the supplied tolerance `atol`. The value corresponding to each key is the respective infeasibility. Infeasibility is defined as the distance between the primal value of the constraint (see `MOI.ConstraintPrimal`) and the nearest point by Euclidean distance in the corresponding set.

## Notes

  * If `skip_missing = true`, constraints containing variables that are not in `point` will be ignored.
  * If `skip_missing = false` and a partial primal solution is provided, an error will be thrown.
  * If no point is provided, the primal solution from the last time the model was solved is used.

## Examples

```jldoctest; setup=:(using JuMP)
julia> model = Model();

julia> @variable(model, 0.5 <= x <= 1);

julia> primal_feasibility_report(model, Dict(x => 0.2))
Dict{Any,Float64} with 1 entry:
  x ≥ 0.5 => 0.3
```
