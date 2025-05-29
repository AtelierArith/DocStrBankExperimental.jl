```
calibratefrompairwisedistances!(net, distances::Matrix{Float64},
    taxon_names::Vector{<:AbstractString})
```

Calibrate the network to match (as best as possible) input pairwise distances between taxa, such as observed from sequence data. `taxon_names` should provide the list of taxa, in the same order in which they they are considered in the `distances` matrix. The optimization criterion is the sum of squares between the observed distances, and the distances from the network (weighted average of tree distances, weighted by γ's). The network's edge lengths are modified.

Warning: for many networks, mutiple calibrations can fit the pairwise distance data equally well (lack of identifiability). This function will output *one* of these equally good calibrations.

optional arguments (default):

  * checkpreorder (true)
  * forceMinorLength0 (false) to force minor hybrid edges to have a length of 0
  * ultrametric (true) to force the network to be

      * time-consistent: all paths from the root to a given node must have the same length, so the age of this node is well-defined, and
      * ultrametric: all tips are at the same distance from the root, so have the same age.
  * NLoptMethod (`:LD_MMA`) for the optimization algorithm. Other options include `:LN_COBYLA` (derivative-free); see NLopt package.
  * tolerance values to control when the optimization is stopped: ftolRel (1e-12), ftolAbs (1e-10) on the criterion, and xtolRel (1e-10), xtolAbs (1e-10) on branch lengths / divergence times.
  * verbose (false)
