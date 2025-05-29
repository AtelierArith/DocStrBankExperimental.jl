```
set_initial_hyperparameters!(model::StateSpaceModel,
                             initial_hyperparameters::Dict{String, <:Real})
```

Fill a model with user inputed initial points for hyperparameter optimzation.

# Example

```jldoctest
julia> model = LocalLevel(rand(100))
LocalLevel

julia> get_names(model)
2-element Vector{String}:
 "sigma2_ε"
 "sigma2_η"

julia> set_initial_hyperparameters!(model, Dict("sigma2_η" => 100.0))
LocalLevel

julia> model.hyperparameters.constrained_values
2-element Vector{Float64}:
 NaN  
 100.0
```
