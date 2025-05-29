```
treeMDP(na, depth; init = "random", branchingfactor = 3)
```

Returns a tree structured MDP with na actions and `depth` of the tree. If `init` is random, the `branchingfactor` determines how many possible states a (action, state) pair has. If `init = "deterministic"` the `branchingfactor = na`.
