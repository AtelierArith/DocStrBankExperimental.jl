# Summary

`struct StandardUpdate <: AbstractUpdate`

A standard update can be a family of calls to [`nni_update!`](@ref), [`branchlength_update!`](@ref), [`root_update!`](@ref), and model updates.

# Constructor

```
StandardUpdate(
    nni::Int,
    branchlength::Int,
    root::Int,
    models::Int,
    refresh::Bool,
    nni_selection::Function,
    branchlength_modifier::UnivariateModifier,
    root_update::RootUpdate,
    models_update::ModelsUpdate
)
```

# Arguments

  * `nni::Int`: the number of times to update the tree by `nni_update!`
  * `branchlength::Int`: the number of times to update the tree by `branchlength_update!`
  * `root::Int`: the number of times to update the tree by `root_update!`
  * `models::Int`: the number of times to update the model
  * `refresh::Bool`: whether to refresh the messages in tree between update operations to ensure message consistency
  * `nni_selection::Function`: the function that selects between nni configurations
  * `branchlength_modifier::UnivariateModifier`: the modifier to update a branchlength by `branchlength_update!`
  * `root_update::RootUpdate`: updates the root by `root_update!`
  * `models_update::ModelsUpdate`: updates the model parameters

See also: [`BayesUpdate`](@ref), [`MaxLikUpdate`](@ref)
