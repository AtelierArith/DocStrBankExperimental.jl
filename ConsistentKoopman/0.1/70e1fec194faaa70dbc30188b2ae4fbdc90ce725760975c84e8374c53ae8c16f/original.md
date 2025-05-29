```
distNN(X::Matrix{Float64}, NN::Integer = 0; usenorm::Function = norm)

computes distances from matrix M, keeps distance (D) and indexing info (N) for NN nearest neighbors

Arguments
=================
- X: data matrix of size nT × nD (time by spatial dim)
- NN: positive nearest neighbors parameter, if 0 defaults to keeping all

Keyword arguments
=================
- usenorm: specify the distance norm to use, defaults to l2
```
