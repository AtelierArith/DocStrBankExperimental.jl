```julia
getTreeCost_02(tree; alpha)

```

Cost function for ranking the structure of a Bayes tree, putting and emphasis on wider but shallower trees by penalizing the average number of siblings. Weighting:     cost = 1/(total num of child / num of parents) *                            (max tree depth) * (max clique dimension)^alpha
