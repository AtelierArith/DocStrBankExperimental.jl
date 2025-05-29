```julia
struct MultivariateGMM
```

A layer which produces a multivariate Gaussian Mixture Model as its output.

# Parameters

  * `outputs::Int64`
  * `mixtures::Int64`
  * `μ::Flux.Dense`
  * `Σ::Flux.Dense`
  * `w::Flux.Chain`
