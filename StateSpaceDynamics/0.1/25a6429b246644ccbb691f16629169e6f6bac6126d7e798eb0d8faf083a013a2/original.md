```
M_Step!(model::ProbabilisticPCA, X::Matrix{<:AbstractFloat}, E_z::Matrix{<:AbstractFloat}, E_zz::Array{<:AbstractFloat, 3}
```

Maximization step of the EM algorithm for PPCA. See Bishop's Pattern Recognition and Machine Learning for more details.

# Args:

  * `model::ProbabilisticPCA`: PPCA model
  * `X::Matrix{<:AbstractFloat}`: Data matrix
  * `E_z::Matrix{<:AbstractFloat}`: E[z]
  * `E_zz::Matrix{<:AbstractFloat}`: E[zz']

# Examples:

```julia
ppca = ProbabilisticPCA(K=1, D=2)
E_z, E_zz = E_Step(ppca, rand(10, 2))
M_Step!(ppca, rand(10, 2), E_z, E_zzᵀ)
```
