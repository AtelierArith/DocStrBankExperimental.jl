```
terms_needed(dim, q_12, stepsize, eps, alg, norm)
```

Used for finite-dimensional approximations of a Q-Wiener process with covariance matrix $Q = Q^\frac{1}{2}*Q^\frac{1}{2}$. Here `q_12` is a vector of the eigenvalues of $Q^\frac{1}{2}$; the square root of the covariance matrix. Equivalently these are the square roots of the eigenvalues of $Q$.

# Examples

```jldoctest; setup=:(using LevyArea)
julia> h = 1/128;

julia> dim = 10;

julia> q = [1/k^2 for k=1:dim];

julia> terms_needed(dim, sqrt.(q), h, h^(3/2), Milstein(), FrobeniusL2())
9
```
