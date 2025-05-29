```
fix_hyperparameters!(model::StateSpaceModel, fixed_hyperparameters::Dict)
```

Fixes the desired hyperparameters so that they are not considered as decision variables in the model estimation.

# Example

```jldoctest
julia> model = LocalLevel(rand(100))
LocalLevel

julia> get_names(model)
2-element Vector{String}:
 "sigma2_ε"
 "sigma2_η"

julia> fix_hyperparameters!(model, Dict("sigma2_ε" => 100.0))
LocalLevel

julia> model.hyperparameters.fixed_constrained_values
Dict{String, Float64} with 1 entry:
  "sigma2_ε" => 100.0
```
