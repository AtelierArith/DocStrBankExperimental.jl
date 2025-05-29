```
fit(DiffMap, data; maxoutdim=2, t=1, α=0.0, ɛ=1.0)
```

Fit a isometric mapping model to `data`.

# Arguments

  * `data::Matrix`: a $d \times n$matrix of observations. Each column of `data` is

an observation, `d` is a number of features, `n` is a number of observations.

# Keyword arguments

  * `kernel::Union{Nothing, Function}`: the kernel function.

It maps two input vectors (observations) to a scalar (a metric of their similarity). by default, a Gaussian kernel. If `kernel` set to `nothing`, we assume `data` is instead the $n \times n$  precomputed Gram matrix.

  * `ɛ::Real=1.0`: the Gaussian kernel variance (the scale parameter). It's ignored if the custom `kernel` is passed.
  * `maxoutdim::Int=2`: the dimension of the reduced space.
  * `t::Int=1`: the number of transitions
  * `α::Real=0.0`: a normalization parameter

# Examples

```julia
X = rand(3, 100)     # toy data matrix, 100 observations

# default kernel
M = fit(DiffMap, X)  # construct diffusion map model
R = transform(M)     # perform dimensionality reduction

# custom kernel
kernel = (x, y) -> x' * y # linear kernel
M = fit(DiffMap, X, kernel=kernel)

# precomputed Gram matrix
kernel = (x, y) -> x' * y # linear kernel
K = ManifoldLearning.pairwise(kernel, eachcol(X), symmetric=true)
M = fit(DiffMap, K, kernel=nothing)
```
