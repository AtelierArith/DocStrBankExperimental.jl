```
clusters_per_cutlevel(distfun::Function, tree::Node, ncuts::Number)
```

Returns:

  * clusts: vector of cluster-memberships. each value indicates the cluster membership of the leaf at that cut.    leaves are ordered in prewalk order within each membership vector
  * treedepths: distance from root for each of the `ncuts`
