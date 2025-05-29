```
gcop2frechet(x::Matrix{Real}, inds::Vector{Int}; naive::Bool = false, rng = Random.GLOBAL_RNG)
```

Takes x the matrix of t realizations of data from the Gaussian n-variate distribution.

Return the matrix of size x, where chosen subset of marginals (determined by inds) has the Frechet (one parameter) sub-copula, all univariate marginals are unchanged. If naive, performs the naive resampling.

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

julia> gcop2frechet(x, [1,2])
6×3 Array{Float64,2}:
 -0.875777   -0.374723   -0.384124
  0.0960334   0.905703   -0.571326
 -0.599792   -0.0110945  -2.3464
  0.813717    1.8513      0.966819
  0.599255    1.56873     0.989712
 -0.7223     -0.172507   -1.54419
```
