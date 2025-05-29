Abstract type `GaussianRandomFieldGenerator`

The following Gaussian random field generators are implemented:

  * `Cholesky`: Cholesky factorization of the covariance matrix, exact but expensive for random fields in dimension `d` > 1
  * `Spectral`: spectral (eigenvalue) decomposition of the covariance matrix, exact but expensive for random fields in dimension `d` > 1
  * `KarhunenLoeve`: Karhunen-Loève expansion, inexact but very efficient for "smooth" random fields when used with a low truncation dimension
  * `CirculantEmbedding`: circulant embedding method, exact and efficient, but can only be used for random fields on structured grids

See also: [`Cholesky`](@ref), [`Spectral`](@ref), [`KarhunenLoeve`](@ref), [`CirculantEmbedding`](@ref)
