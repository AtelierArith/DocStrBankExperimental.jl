```
KMeansTreeOptions <: TreeOptions
```

Is the datatype that describes which tree the [`create_tree`](@ref) function creates.

# Fields

  * `iterations`: number of iterations on each level, default is one iterations
  * `nchildren`: defines the number of children of each node, default is two
  * `nmin`: defines the minimum amount of datapoints which are needed in a    cluster so that it gets split up in subclusters, default is 1
  * `maxlevel`: defines the maximum amount of levels, default is 100.
  * `algorithm`: defines which algorithm is used. The :naive approach is not recommended.   Default is the wrapped ParallelKMeans algorithm.
