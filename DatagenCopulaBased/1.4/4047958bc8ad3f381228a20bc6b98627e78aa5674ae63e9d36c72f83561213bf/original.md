```
gcop2arch(x::Matrix{Real}, inds::Vector{Pair{String,Vector{Int64}}}; naive::Bool = false, notnested::Bool = false, rng = Random.GLOBAL_RNG)
```

Takes x the matrix of t realizations of data from Gaussian n-variate distribution. Return a matrix of size x, where chosen subset of marginals (inds[i][2]) has an Archimedean sub-copula (denoted by inds[i][1]), all univariate marginals are unchanged.

For example inds = ["clayton" => [1,2]] means that the subset of marginals indexed by 1,2 will be changed to the Clayton sub-copula. Inds may have more elements but marginals must not overlap.

If naive, the naive resampling will be used. In notnested nested Archimedean copulas will not be used.

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

julia> gcop2arch(x, ["clayton" => [1,2]]; naive::Bool = false, notnested::Bool = false)
6×3 Array{Float64,2}:
 -0.742443   0.424851  -0.384124
  0.211894   0.195774  -0.571326
 -0.989417  -0.299369  -2.3464
  0.157683   1.47768    0.966819
  0.154893   0.893253   0.989712
 -0.657297  -0.339814  -1.54419
```
