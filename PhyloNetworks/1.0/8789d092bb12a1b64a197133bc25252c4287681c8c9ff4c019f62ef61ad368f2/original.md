```
parsimonysoftwired(net, tipdata)
parsimonysoftwired(net, species, sequences)
```

Calculate the most parsimonious (MP) score of a network given a discrete character at the tips. The softwired parsimony concept is used: where the number of state transitions is minimized over all trees displayed in the network.

Data can given in one of the following:

  * `tipdata`: data frame for a single trait, in which case the taxon names  are to appear in column 1 or in a column named "taxon" or "species", and  trait values are to appear in column 2 or in a column named "trait".
  * `tipdata`: dictionary taxon => state, for a single trait.
  * `species`: array of strings, and `sequences`: array of sequences,  in the order corresponding to the order of species names.

## algorithm

The dynamic programming algorithm by Fischer et al. (2015) is used. The function loops over all the displayed subtrees within a blob (biconnected component), so its complexity is of the order of `n * m * c^2 * 2^level` where `n` is the number of tips, `m` the number of traits, `c` the number of states, and `level` is the level of the network: the maximum number of hybridizations within a blob.

See [`parsimonyGF`](@ref) for a different algorithm, slower but extendable to other parsimony criteria.

## references

1. Fischer, M., van Iersel, L., Kelk, S., Scornavacca, C. (2015). On computing the Maximum Parsimony score of a phylogenetic network. SIAM J. Discrete Math., 29(1):559-585.
