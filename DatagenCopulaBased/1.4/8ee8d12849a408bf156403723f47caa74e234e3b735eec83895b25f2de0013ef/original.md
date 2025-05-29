```
gcop2marshallolkin(x::Matrix{Real}, inds::Vector{Int}, λ1::Real = 1., λ2::Real = 1.5; naive::Bool = false, rng = Random.GLOBAL_RNG)
```

Takes x the matrix of t realizations of data from Gaussian n-variate distribution.

Return a matrix of size x, where chosen subset of marginals (inds) has bi-variate Marshall-Olkin sub-copula parameterized by the free parameters λ1 and λ2. λ12 is computed form the correlation between marginals. All univariate marginals are unchanged. If naive, uses the naive resampling.

```jldoctest

julia> Σ = [1. 0.5 0.5; 0.5 1. 0.5; 0.5 0.5 1];

julia> Random.seed!(42)

julia> x = rand(MvNormal(Σ), 6)'
6×3 Array{Float64,2}:
 -0.556027  -0.662861   -0.384124
 -0.299484   1.38993    -0.571326
 -0.468606  -0.0990787  -2.3464
  1.00331    1.43902     0.966819
  0.518149   1.55065     0.989712
 -0.886205   0.149748   -1.54419

julia> gcop2marshallolkin(x, [1,2], 1., 1.5; naive = false)
6×3 Array{Float64,2}:
 -0.790756   0.784371  -0.384124
 -0.28088    0.338086  -0.571326
 -0.90688   -0.509684  -2.3464
  0.738628   1.71026    0.966819
  0.353654   1.19357    0.989712
 -0.867606  -0.589929  -1.54419
```
