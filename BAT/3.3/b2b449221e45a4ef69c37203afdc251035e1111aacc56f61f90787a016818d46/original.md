```
struct PosteriorMeasure{Li,Pr<:AbstractMeasure} <: AbstractPosteriorMeasure
```

A representation of a PosteriorMeasure, based a likelihood and prior. Likelihood and prior be accessed via

```julia
getlikelihood(posterior::PosteriorMeasure)::Li
getprior(posterior::PosteriorMeasure)::Pr
```

Constructors:

  * `PosteriorMeasure(likelihood, prior)`
  * `PosteriorMeasure{T<:Real}(likelihood, prior)`

Fields:

  * `likelihood::Any`
  * `prior::MeasureBase.AbstractMeasure`
