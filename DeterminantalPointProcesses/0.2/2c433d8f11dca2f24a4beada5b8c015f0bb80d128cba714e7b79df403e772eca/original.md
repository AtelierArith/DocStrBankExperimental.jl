```
rand([rng::AbstractRNG], dpp::DeterminantalPointProcess)::Vector{Int}
rand([rng::AbstractRNG], dpp::DeterminantalPointProcess, n::Int)::Vector{Vector{Int}}
```

Exact sampling from a DPP [1]. Returns a vector of indices with respect to the `L` matrix passed to the `DeterminantalPointProcess`. The length of each vector can vary from 0 to the `size(L,1)`
