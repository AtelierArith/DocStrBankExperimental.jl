`struct NormalSpline{T, RK} <: AbstractSpline where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

Define a structure containing full information of a normal spline

# Fields

  * `_kernel`: a reproducing kernel spline was built with
  * `_compression`: factor of transforming the original node locations into unit hypercube
  * `_nodes`: transformed function value nodes
  * `_values`: function values at interpolation nodes
  * `_d_nodes`: transformed function directional derivative nodes
  * `_es`: normalized derivative directions
  * `_d_values`: function directional derivative values
  * `_min_bound`: minimal bounds of the original node locations area
  * `_gram`: Gram matrix of the problem
  * `_chol`: Cholesky factorization of the Gram matrix
  * `_mu`: spline coefficients
  * `_cond`: estimation of the Gram matrix condition number
