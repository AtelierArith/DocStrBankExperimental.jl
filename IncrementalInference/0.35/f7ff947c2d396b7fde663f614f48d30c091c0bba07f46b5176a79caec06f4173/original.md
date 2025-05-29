```julia
attemptTreeSimilarClique(othertree, seeksSimilar)

```

Special internal function to try return the clique data if succesfully identified in `othertree::AbstractBayesTree`, based on contents of `seeksSimilar::BayesTreeNodeData`.

Notes

  * Used to identify and skip similar cliques (i.e. recycle computations)
