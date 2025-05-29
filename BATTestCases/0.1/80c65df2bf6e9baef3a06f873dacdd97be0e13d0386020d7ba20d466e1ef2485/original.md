```
MultimodalStudentT <: Distribution{Multivariate,Continuous}
```

The Multimodal Student-t Distribution (It's defined similarly to multimodal Cauchy defined in [Caldwell et al.](https://arxiv.org/abs/1808.08051)).

Assumes two bimodal peaks, each in its own dimension.

Constructors:

  * `MultimodalStudentT(; μ::Real=1, σ::Float64=0.2, ν::Integer=1, n::Integer=4)`

Arguments:

  * `μ::Real`: The location parameter used for the two bimodal peaks.
  * `σ::Float64`: The scale parameter shared among all components.
  * `ν::Int`: The degrees of freedom.
  * `n::Int`: The number of dimensions.

Fields:

  * `bimodals::Distributions.MixtureModel`
  * `σ::Float64`
  * `n::Int64`
  * `dist::Distributions.Product`

!!! note
    All fields of `MultimodalStudentT` are considered internal and subject to change without deprecation.

