An abstract type for a surrogate model approximating the objective function.

Example usage: `struct CustomModel <: SurrogateModel ... end`

All models *should* implement:

  * `make_discrete(model::CustomModel, discrete::AbstractVector{<:Bool}) -> discrete_model::CustomModel`
  * `model_posterior(model::CustomModel, data::ExperimentDataMAP) -> (x -> mean, std)`
  * `model_loglike(model::CustomModel, data::ExperimentData) -> (::ModelParams -> ::Real)`
  * `sample_params(model::CustomModel) -> ::ModelParams`
  * `param_priors(model::CustomModel) -> ::ParamPriors`

Models *may* implement:

  * `sliceable(::CustomModel) -> ::Bool`
  * `model_posterior_slice(model::CustomModel, data::ExperimentDataMAP, slice::Int) -> (x -> mean, std)`

If `sliceable(::CustomModel) == true`, then the model *should* additionally implement:

  * `model_loglike_slice(model::SliceableModel, data::ExperimentData, slice::Int) -> (::ModelParams -> ::Real)`
  * `θ_slice(model::SliceableModel, idx::Int) -> Union{Nothing, UnitRange{<:Int}}`

See also: [`LinModel`](@ref), [`NonlinModel`](@ref), [`GaussianProcess`](@ref), [`Semiparametric`](@ref)
