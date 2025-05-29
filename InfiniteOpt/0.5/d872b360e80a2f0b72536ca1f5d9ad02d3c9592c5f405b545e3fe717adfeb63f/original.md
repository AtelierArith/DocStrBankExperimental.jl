```
JuMP.set_objective_function(model::InfiniteModel, func::Real)::Nothing
```

Extend `JuMP.set_objective_function` to set the objective expression of `model` with a number.

**Example**

```jldoctest; setup = :(using InfiniteOpt, JuMP; model = InfiniteModel())
julia> set_objective_function(model, 3)

julia> objective_function(model)
3
```
