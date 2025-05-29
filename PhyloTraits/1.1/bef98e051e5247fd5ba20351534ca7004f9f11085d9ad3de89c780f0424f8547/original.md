```
ancestralreconstruction(net::HybridNetwork, Y::Vector, params::ParamsBM)
```

Compute the conditional expectations and variances of the ancestral (un-observed) traits values at the internal nodes of the phylogenetic network (`net`), given the values of the traits at the tips of the network (`Y`) and some known parameters of the process used for trait evolution (`params`, only BM with fixed root works for now).

This function assumes that the parameters of the process are known. For a more general function, see `ancestralreconstruction(obj::PhyloNetworkLinearModel[, X_n::Matrix])`.
