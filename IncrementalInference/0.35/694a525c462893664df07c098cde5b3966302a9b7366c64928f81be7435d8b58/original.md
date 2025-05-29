```julia
getTreeCost_01(tree; alpha)

```

Simple cost function for ranking the structure of a Bayes tree. Weighting:     cost = (max tree depth) * (max clique dimension)^alpha
