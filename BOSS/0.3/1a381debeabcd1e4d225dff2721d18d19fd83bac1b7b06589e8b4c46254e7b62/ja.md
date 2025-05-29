目的関数を近似するためのサロゲートモデルの抽象型。

使用例: `struct CustomModel <: SurrogateModel ... end`

すべてのモデルは*実装するべき*です：

  * `make_discrete(model::CustomModel, discrete::AbstractVector{<:Bool}) -> discrete_model::CustomModel`
  * `model_posterior(model::CustomModel, data::ExperimentDataMAP) -> (x -> mean, std)`
  * `model_loglike(model::CustomModel, data::ExperimentData) -> (::ModelParams -> ::Real)`
  * `sample_params(model::CustomModel) -> ::ModelParams`
  * `param_priors(model::CustomModel) -> ::ParamPriors`

モデルは*実装するかもしれません*：

  * `sliceable(::CustomModel) -> ::Bool`
  * `model_posterior_slice(model::CustomModel, data::ExperimentDataMAP, slice::Int) -> (x -> mean, std)`

もし `sliceable(::CustomModel) == true` であれば、モデルは*さらに実装するべき*です：

  * `model_loglike_slice(model::SliceableModel, data::ExperimentData, slice::Int) -> (::ModelParams -> ::Real)`
  * `θ_slice(model::SliceableModel, idx::Int) -> Union{Nothing, UnitRange{<:Int}}`

参照： [`LinModel`](@ref), [`NonlinModel`](@ref), [`GaussianProcess`](@ref), [`Semiparametric`](@ref)
