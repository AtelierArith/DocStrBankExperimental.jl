```
loglikelihood(x0::Matrix{T}, arnet::ArNet) where {T<:Integer})
```

Return the vector of loglikelihoods computed from `Matrix` `x0` under the model `arnet`. `size(x0) == N,M` where `N` is the sequences length, and `M` the number of sequences. The returned vector has `M` elements.
