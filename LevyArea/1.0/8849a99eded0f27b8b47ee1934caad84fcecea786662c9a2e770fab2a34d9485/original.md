```
iterated_integrals(W::AbstractVector, q_12::AbstractVector, h, eps; 
    ito_correction=true,
    error_norm=FrobeniusL2(),
    alg=optimal_algorithm(length(W),q_12,h,eps,error_norm)
)
```

Simulates an approximation of the iterated stochastic integrals for finite-dimensional approximations of a Q-Wiener process with covariance matrix $Q = Q^\frac{1}{2}*Q^\frac{1}{2}$. Here `q_12` is a vector of the eigenvalues of $Q^\frac{1}{2}$; the square root of the covariance matrix. Equivalently these are the square roots of the eigenvalues of $Q$.

# Examples

```jldoctest; setup=:(using LinearAlgebra; using LevyArea)
julia> h = 0.01; dim=10; q = [1/k^2 for k=1:dim];

julia> W = √h * sqrt.(q) .* randn(dim);

julia> diag(iterated_integrals(W,sqrt.(q),h,h^(3/2))) ≈ 0.5*W.^2 .- 0.5*h*q
true
```
