```
construct_workspace(prob::MixtureIntervalProbabilities)
```

Construct a workspace for computing the Bellman update, given a value function. If the Bellman update is used in a hot-loop, it is more efficient to use this function to preallocate the workspace and reuse across iterations.

The workspace type is determined by the type and size of the transition probability matrix, as well as the number of threads available.
