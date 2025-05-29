```
parsimonyGF(net, tip_dictionary, criterion=:softwired)
parsimonyGF(net, species, sequenceData, criterion=:softwired)
```

Calculate the most parsimonious score of a network given discrete characters at the tips using a general framework (Van Iersel et al. 2018) allowing for various parsimony criteria: softwired (default), hardwired, parental etc. Only softwired is implemented at the moment.

Data can given in one of the following:

  * `tipdata`: data frame for a single trait, in which case the taxon names  are to appear in column 1 or in a column named "taxon" or "species", and  trait values are to appear in column 2 or in a column named "trait".
  * `tipdata`: dictionary taxon => state, for a single trait.
  * `species`: array of strings, and `sequences`: array of sequences,   in the order corresponding to the order of species names.

## algorithm

The complexity of the algorithm is exponential in the level of the network, that is, the maximum number of hybridizations in a single blob, or biconnected component (Fischer et al. 2015). The function loops over all the state assignments of the minor parent of each hybrid node within a blob, so its complexity is of the order of `n * m * c^2 * c^level` where `n` is the number of tips, `m` the number of traits and `c` the number of states.

See [`parsimonysoftwired`](@ref) for a faster algorithm, but solving the softwired criterion only.

## references

1. Leo Van Iersel, Mark Jones, Celine Scornavacca (2017). Improved Maximum Parsimony Models for Phylogenetic Networks, Systematic Biology, (https://doi.org/10.1093/sysbio/syx094).
2. Fischer, M., van Iersel, L., Kelk, S., Scornavacca, C. (2015). On computing the Maximum Parsimony score of a phylogenetic network. SIAM J. Discrete Math., 29(1):559-585.

Use the recursive helper function [`parsimonyGF_bottomup!`](@ref). Use the fields `ischild1`, `booln4` to know which nodes are at the root of a blob, and `boole2` to know which edges are cut (below the minor parent of each hybrid).
