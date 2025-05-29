```
getphylodiv(tree::ChronoTree, tipset; keeproot::Bool=false)
```

Compute the phylogenetic diversity (PD) of a given set of tips of the tree,  i.e., the sum of branch lengths of the subtree generated from the set. 

The argument `keeproot` controls whether the original root node needs to be  contained in the subtree; by default it is set to `false`.
