```
gcop2tstudent(x::Matrix{Real}, ind::Vector{Int}, ν::Int; naive::Bool = false)
```

Takes x the matrix of t realizations of data from Gaussian n-variate distribution.

Return the matrix of size x, where chosen subset of marginals (indexed by ind) has the t-Student copula with ν degrees of freedom, all univariate marginals are unchanged. If naive, performs the naive resampling.

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

julia> gcop2tstudent(x, [1,2], 6)
6×3 Array{Float64,2}:
 -0.514449  -0.49147    -0.384124
 -0.377933   1.66254    -0.571326
 -0.430426  -0.0165044  -2.3464
  0.928668   1.50472     0.966819
  0.223439   1.12372     0.989712
 -0.710786   0.239012   -1.54419
```
