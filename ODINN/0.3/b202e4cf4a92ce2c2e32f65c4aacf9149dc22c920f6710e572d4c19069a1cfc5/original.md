```
Model(; iceflow::Union{IFM, Vector{IFM}, Nothing}, mass_balance::Union{MBM, Vector{MBM}, Nothing}, machine_learning::Union{MLM, Nothing}) where {IFM <: IceflowModel, MBM <: MBmodel, MLM <: MLmodel}
```

Creates a new model instance using the provided iceflow, mass balance, and machine learning components.

# Arguments

  * `iceflow::Union{IFM, Vector{IFM}, Nothing}`: The iceflow model(s) to be used. Can be a single model, a vector of models, or `nothing`.
  * `mass_balance::Union{MBM, Vector{MBM}, Nothing}`: The mass balance model(s) to be used. Can be a single model, a vector of models, or `nothing`.
  * `machine_learning::Union{MLM, Nothing}`: The machine learning model to be used. Can be a single model or `nothing`.

# Returns

  * `model`: A new instance of `Sleipnir.Model` initialized with the provided components.
