```
snaq!(T::HybridNetwork, d::DataCF)
```

Estimate the network (or tree) to fit observed quartet concordance factors (CFs) stored in a DataCF object, using maximum pseudo-likelihood. A level-1 network is assumed. The search starts from topology `T`, which can be a tree or a network with no more than `hmax` hybrid nodes. The function name ends with ! because it modifies the CF data `d` by updating its attributes `expCF`: CFs expected under the network model. It does *not* modify `T`. The quartet pseudo-deviance is the negative log pseudo-likelihood, up to an additive constant, such that a perfect fit corresponds to a deviance of 0.0.

Output:

  * estimated network in file `.out` (also in `.log`): best network overall and list of networks from each individual run.
  * the best network and modifications of it, in file `.networks`. All networks in this file have the same undirected topology as the best network, but have different hybrid/gene flow directions. These other networks are reported with their pseudo-likelihood scores, because non-identifiability issues can cause them to have very similar scores, and because SNaQ was shown to estimate the undirected topology accurately but not the direction of hybridization in cases of near non-identifiability.
  * if any error occurred, file `.err` provides information (seed) to reproduce the error.

There are many optional arguments, including

  * `hmax` (default 1): maximum number of hybridizations allowed
  * `verbose` (default false): if true, print information about the numerical optimization
  * `runs` (default 10): number of independent starting points for the search
  * `outgroup` (default none): outgroup taxon to root the estimated topology at the very end
  * `filename` (default "snaq"): root name for the output files (`.out`, `.err`). If empty (""), files are *not* created, progress log goes to the screen only (standard out).
  * `seed` (default 0 to get it from the clock): seed to replicate a given search
  * `probST` (default 0.3): probability to start from `T` at each given run. With problability 1-probST, the search is started from an NNI modification of `T` along a tree edge with no hybrid neighbor, with a possible modification of one reticulation if `T` has one.
  * `updateBL` (default true): If true and if `T` is a tree, the branch lengths in `T` are first optimized roughly with [`updateBL!`](@ref) by using the average CF of all quartets defining each branch and back-calculating the coalescent units.

The following optional arguments control when to stop the optimization of branch lengths and γ's on each individual candidate network. Defaults are in parentheses:

  * `ftolRel` (1e-6) and `ftolAbs` (1e-6): relative and absolute differences of the network score between the current and proposed parameters,
  * `xtolRel` (1e-2) and `xtolAbs` (1e-3): relative and absolute differences between the current and proposed parameters.

Greater values will result in a less thorough but faster search. These parameters are used when evaluating candidate networks only. The following optional arguments control when to stop proposing new network topologies:

  * `Nfail` (75): maximum number of times that new topologies are proposed and rejected (in a row).
  * `liktolAbs` (1e-6): the proposed network is accepted if its score is better than the current score by at least liktolAbs.

Lower values of `Nfail` and greater values of `liktolAbs` and `ftolAbs` would result in a less thorough but faster search.

At the end, branch lengths and γ's are optimized on the last "best" network with different and very thorough tolerance parameters: 1e-12 for `ftolRel`, 1e-10 for `ftolAbs`, `xtolRel`, `xtolAbs`.

See also: [`topologymaxQpseudolik!`](@ref) to optimize parameters on a fixed topology, and [`topologyQpseudolik!`](@ref) to get the deviance (pseudo log-likelihood up to a constant) of a fixed topology with fixed parameters.

Reference:   Claudia Solís-Lemus and Cécile Ané (2016). Inferring phylogenetic networks with maximum pseudolikelihood under incomplete lineage sorting. [PLoS Genetics 12(3):e1005896](http://journals.plos.org/plosgenetics/article?id=10.1371/journal.pgen.1005896)
