```julia
struct PersonParameterResult{T<:AbstractItemResponseModels.ItemResponseModel, U<:PersonParameters.PersonParameter, V<:PersonParameters.PersonParameterAlgorithm} <: AbstractArray{U<:PersonParameters.PersonParameter, 1}
```

A collection of estimated person parameters.

## Fields

  * `values`: A vector of estimated person parameters
  * `algorithm`: The algorithm used for estimation

## Methods

  * [`modeltype`](@ref): Get the model type of the scaling model
  * [`algorithm`](@ref): Get the algorithm used for estimation
