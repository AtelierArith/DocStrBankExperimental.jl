```
loglikelihood(arnet::ArNet, arvar::ArVar)
```

Return the vector of loglikelihoods computed from `arvar.Z` under the model `arnet`. `size(arvar.Z) == N,M` where `N` is the sequences length, and `M` the number of sequences. The returned vector has `M` elements reweighted by `arvar.W`
