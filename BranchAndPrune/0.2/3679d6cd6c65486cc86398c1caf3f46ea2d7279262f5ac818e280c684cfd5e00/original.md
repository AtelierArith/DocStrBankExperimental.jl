```
bpsearch(bp::BranchAndPruneSearch ; callback::Function)
```

Perform a branch and prune search and return its result as a BranchAndPruneResult.

A callback function can be given, which is called on the search state at every iteration. It must have signature `callback(state::SearchState)::Bool`. If it return `true` the searched is stopped and return.
