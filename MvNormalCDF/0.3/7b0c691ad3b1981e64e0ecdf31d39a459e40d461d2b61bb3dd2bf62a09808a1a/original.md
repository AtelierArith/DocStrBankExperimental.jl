```
mvnormcdf(μ::AbstractVector, Σ::AbstractMatrix, a::AbstractVector, b::AbstractVector; m::Integer = 1000*size(Σ,1), rng = RandomDevice())
```

Computes the Multivariate Normal probability integral using a quasi-Monte-Carlo algorithm with m points for positive definite covariance matrix Σ, mean [0,...], with lower integration limit vector a and upper integration limit vector b.

$$
\Phi_k(\mathbf{a},\mathbf{b},\mathbf{\Sigma} ) = \frac{1}{\sqrt{\left | \mathbf{\Sigma}  \right |{(2\pi )^k}}}\int_{a_1}^{b_1}\int_{a_2}^{b_2}\begin{align*}
 &...\end{align*} \int_{a_k}^{b_k}e^{^{-\frac{1}{2}}\mathbf{x}^t{\mathbf{\Sigma }}^{-1}\boldsymbol{\mathbf{x}}}dx_k...dx_1
$$

Probability p is output with error estimate e.

# Arguments

  * `μ::AbstractVector`: vector of means
  * `Σ::AbstractMatrix`: positive-definite covariance matrix of MVN distribution
  * `a::AbstractVector`: lower integration limit column vector
  * `b::AbstractVector`: upper integration limit column vector
  * `m::Integer`:        number of integration points (default 1000*dimension)
  * `rng`: random number generator

# Example

```julia
Σ = [4 3 2 1; 3 5 -1 1; 2 -1 4 2; 1 1 2 5]
μ = zeros(4)
a = [-Inf; -Inf; -Inf; -Inf]
b = [1; 2; 3; 4]
m = 5000
(p,e) = mvnormcdf(μ, Σ, a, b; m=m)
#(0.605219554009911, 0.0015718064928452481)
```

Results will vary slightly from run-to-run due to the quasi-Monte-Carlo algorithm.
