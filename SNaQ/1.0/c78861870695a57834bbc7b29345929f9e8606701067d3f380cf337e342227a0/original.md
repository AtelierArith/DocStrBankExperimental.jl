```
bootsnaq(T::HybridNetwork, df::DataFrame)
bootsnaq(T::HybridNetwork, vector of tree lists)
```

Bootstrap analysis for SNaQ. Bootstrap data can be quartet concordance factors (CF), drawn from sampling uniformly in their credibility intervals, as given in the data frame `df`. Alternatively, bootstrap data can be gene trees sampled from a vector of tree lists: one list of bootstrap trees per locus (see [`readmultinewick_files`](https://juliaphylo.github.io/PhyloNetworks.jl/stable/lib/public/#PhyloNetworks.readmultinewick_files-Tuple{AbstractString}) in `PhyloNetworks` to generate this, from a file containing a list of bootstrap files: one per locus).

From each bootstrap replicate, a network is estimated with [`snaq!`](@ref), with a search starting from topology `T`. Optional arguments include the following, with default values in parentheses:

  * `hmax` (1): max number of reticulations in the estimated networks
  * `nrep` (10): number of bootstrap replicates.
  * `runs` (10): number of independent optimization runs for each replicate
  * `filename` ("bootsnaq"): root name for output files. No output files if "".
  * `seed` (0 to get a random seed from the clock): seed for random number generator
  * `otherNet` (empty): another starting topology so that each replicate will start prcnet% runs on otherNet and (1-prcnet)% runs on `T`
  * `prcnet` (0): percentage of runs starting on `otherNet`; error if different than 0.0, and otherNet not specified.
  * `ftolRel`, `ftolAbs`, `xtolRel`, `xtolAbs`, `liktolAbs`, `Nfail`, `probST`, `verbose`, `outgroup`: see `snaq!`, same defaults.

If `T` is a tree, its branch lengths are first optimized roughly with [`updateBL!`](@ref) (by using the average CF of all quartets defining each branch and calculating the coalescent units corresponding to this quartet CF). If `T` has one or more reticulations, its branch lengths are taken as is to start the search. The branch lengths of `otherNet` are always taken as is to start the search.
