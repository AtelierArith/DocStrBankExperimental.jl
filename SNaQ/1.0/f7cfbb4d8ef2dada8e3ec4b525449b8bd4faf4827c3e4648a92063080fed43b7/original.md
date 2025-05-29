```
topologyQpseudolik!(net::HybridNetwork, d::DataCF)
```

Calculate the quartet pseudo-deviance of a given network/tree for DataCF `d`. This is the negative log pseudo-likelihood, up to an additive constant, such that a perfect fit corresponds to a deviance of 0.0.

Note that the network's parameters (edge lengths and γs) are *not* optimized. So be careful if `net` does not have all internal branch lengths specified, because then the pseudolikelihood will be meaningless. See [`topologymaxQpseudolik!`](@ref) if you want branch lengths and numerical parameters optimized on the given network.

The loglik value of the network is updated, and `d` is updated with the expected concordance factors under the input network.
