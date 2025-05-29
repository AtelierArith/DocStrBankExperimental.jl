```
rand([rng::AbstractRNG], kdpp::kDeterminantalPointProcess)::Vector{Int}
rand([rng::AbstractRNG], kdpp::kDeterminantalPointProcess, n::Int)::Vector{Vector{Int}}
```

Exact sampling from a k-DPP [1]. Returns a vector of indices with respect to the `L` matrix passed to the `kDeterminantalPointProcess` Each vector is of size `k`.
