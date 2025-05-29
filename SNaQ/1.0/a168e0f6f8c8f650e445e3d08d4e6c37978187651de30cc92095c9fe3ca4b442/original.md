```
topologymaxQpseudolik!(
    net::HybridNetwork,
    d::DataCF;
    verbose = true,
    ftolRel = 1e-6,
    ftolAbs = 1e-6,
    xtolRel = 1e-2,
    xtolAbs = 1e-3
)
```

Estimate the branch lengths and inheritance probabilities (γ's) for a given network topology. The network is *not* modified, only the object `d` is, with updated expected concordance factors.

Ouput: new network, with optimized parameters (branch lengths and gammas). The maximized quartet pseudo-deviance is the negative log pseudo-likelihood, up to an additive constant, such that a perfect fit corresponds to a deviance of 0.0. This is also an attribute of the network, which can be accessed with `loglik(net)`.

Optional arguments:

  * `verbose`: if `true`, information on the numerical optimization is printed to screen
  * `ftolRel`, `ftolAbs`, `xtolRel`, `xtolAbs`: absolute and relative tolerance values for the pseudo-deviance function (`f`) and the parameters (`x`).

The default tolerance values are quite lenient, for faster running time. They are more lenient than those used in `snaq!`, so we can expect that `snaq!` returns a better (lower) score for the same network topology. It is *highly* recommended to use more stringent value than the default, for example 1e-12 for `ftolRel`, and 1e-10 for `ftolAbs`, `xtolRel`, `xtolAbs` to match those in [`snaq!`](@ref).

To further optimize branch lengths and γs, another strategy is the run the `topologymaxQpseudolik!` multiple times, because each time the edge parameters in the network are improved, and re-starting a search from a good place leads to finding even better edge parameter values. If `snaq!` finds a better score for the given network topology, then using this strategy (effectively used by `snaq!` when optimizing edge parameters at each trial) and using stringent tolerances should eliminate the difference.
