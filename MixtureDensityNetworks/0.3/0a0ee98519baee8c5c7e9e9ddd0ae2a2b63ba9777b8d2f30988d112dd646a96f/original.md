```julia
struct UnivariateGMM
```

A layer which produces a univariate Gaussian Mixture Model as its output.

# Parameters

  * `μ::Flux.Dense`
  * `Σ::Flux.Dense`
  * `w::Flux.Chain`
