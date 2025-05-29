```
E_Step(ppca::ProbabilisticPCA, X::Matrix{<:AbstractFloat})
```

Expectation step of the EM algorithm for PPCA. See Bishop's Pattern Recognition and Machine Learning for more details.

# Args:

  * `ppca::ProbabilisticPCA`: PPCA model
  * `X::Matrix{<:AbstractFloat}`: Data matrix

# Examples:

```julia
ppca = ProbabilisticPCA(K=1, D=2)
E_Step(ppca, rand(10, 2))
```
