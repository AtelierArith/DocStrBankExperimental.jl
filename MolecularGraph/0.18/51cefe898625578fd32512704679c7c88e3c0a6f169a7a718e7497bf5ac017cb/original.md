```
tdmcis(mol1::MolGraph, mol2::MolGraph; kwargs...) -> (Dict, Symbol)
tdmces(mol1::MolGraph, mol2::MolGraph; kwargs...) -> (Dict, Symbol)
```

Compute disconnected MCS of mol1 and mol2 with topological constraint (td-MCS).

## Keyword arguments

  * diameter(Int): distance cutoff for topological constraint.
  * tolerance(Int): distance mismatch tolerance for topological constraint.
  * timeout(Real): abort calculation and return suboptimal results if the execution

time has reached the given value (default=60, in seconds).

  * targetsize(Int): abort calculation and return suboptimal result so far if the

given mcs size achieved.

# References

1. Kawabata, T. (2011). Build-Up Algorithm for Atomic Correspondence between

Chemical Structures. Journal of Chemical Information and Modeling, 51(8), 1775–1787. https://doi.org/10.1021/ci2001023

1. https://www.jstage.jst.go.jp/article/ciqs/2017/0/2017*P4/*article/-char/en
