**Univariate**

```
sampleMeasure(n::Int,name::String,w::Function,dom::Tuple{<:Real,<:Real},symm::Bool,d::Dict;method::String="adaptiverejection")
sampleMeasure(n::Int,m::Measure;method::String="adaptiverejection")
sampleMeasure(n::Int,op::AbstractOrthoPoly;method::String="adaptiverejection")
```

Draw `n` samples from the measure `m` described by its

  * `name`
  * weight function `w`,
  * domain `dom`,
  * symmetry property `symm`,
  * and, if applicable, parameters stored in the dictionary `d`. By default, an adaptive rejection sampling method is used (from [AdaptiveRejectionSampling.jl](https://github.com/mauriciogtec/AdaptiveRejectionSampling.jl)), unless it is a common random variable for which [Distributions.jl](https://github.com/JuliaStats/Distributions.jl) is used.

The function is dispatched to accept `AbstractOrthoPoly`.

**Multivariate**

```
sampleMeasure(n::Int,m::ProductMeasure;method::Vector{String}=["adaptiverejection" for i=1:length(m.name)])
sampleMeasure(n::Int,mop::MultiOrthoPoly;method::Vector{String}=["adaptiverejection" for i=1:length(mop.meas.name)])
```

Multivariate extension, which provides an array of samples with `n` rows and as many columns as the multimeasure has univariate measures.
