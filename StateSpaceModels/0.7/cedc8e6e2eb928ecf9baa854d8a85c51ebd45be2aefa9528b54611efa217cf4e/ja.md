```
fix_hyperparameters!(model::StateSpaceModel, fixed_hyperparameters::Dict)
```

モデル推定において、望ましいハイパーパラメータを固定し、意思決定変数として考慮されないようにします。

# 例

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
