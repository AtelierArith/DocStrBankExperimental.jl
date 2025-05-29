```julia
calcProductGaussians(
    M,
    μ_,
    Σ_;
    μ0,
    Λ_,
    weight,
    do_transport_correction
)

```

Calculate covariance weighted mean as product of incoming Gaussian points $μ_$ and coordinate covariances $Σ_$.

Notes

  * Return both weighted mean and new covariance (teh congruent product)
  * More efficient helper function allows passing keyword inverse covariances `Λ_` instead.
  * Assume `size(Σ_[1],1) == manifold_dimension(M)`.
  * calc lambdas first and use to calculate mean product second.
  * https://ccrma.stanford.edu/~jos/sasp/Product*Two*Gaussian_PDFs.html
  * Pennec, X. Intrinsic Statistics on Riemannian Manifolds: Basic Tools for Geometric Measurements, HAL Archive, 2011, Inria, France.

DevNotes:

  * FIXME is parallel transport needed as products involve covariances from different tangent spaces?
  * TODO avoid recomputing covariance matrix inverses all the time
