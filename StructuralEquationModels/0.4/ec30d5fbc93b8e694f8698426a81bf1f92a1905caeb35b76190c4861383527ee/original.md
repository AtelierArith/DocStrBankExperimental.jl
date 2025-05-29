```
(1) SemEnsemble(models...; weights = nothing, kwargs...)

(2) SemEnsemble(;specification, data, groups, column = :group, kwargs...)
```

Constructor for ensemble models. (2) can be used to conveniently specify multigroup models.

# Arguments

  * `models...`: `AbstractSem`s.
  * `weights::Vector`:  Weights for each model. Defaults to the number of observed data points.
  * `specification::EnsembleParameterTable`: Model specification.
  * `data::DataFrame`: Observed data. Must contain a `column` of type `Vector{Symbol}` that contains the group.
  * `groups::Vector{Symbol}`: Group names.
  * `column::Symbol`: Name of the column in `data` that contains the group.

All additional kwargs are passed down to the model parts.

Returns a SemEnsemble with fields

  * `n::Int`: Number of models.
  * `sems::Tuple`: `AbstractSem`s.
  * `weights::Vector`: Weights for each model.
  * `param_labels::Vector`: Stores parameter labels and their position.

For instructions on multigroup models, see the online documentation.
