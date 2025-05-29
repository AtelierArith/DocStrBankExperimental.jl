```
nndescent(GraphT::Type{ApproximateKNNGraph}, data, n_neighbors, metric; kwargs...)
```

Find the approximate neighbors of each point in `data` by  iteratively refining a KNN graph of type `GraphT`. Returns the final KNN graph.

# Keyword Arguments

  * `max_iters = 10`: Limits the number of iterations to refine candidate

nearest neighbors. Higher values trade off speed for accuracy. Note that graph construction may terminate early if little progress is being made.

  * `sample_rate = 1`: The sample rate for calculating *local joins*

around each point. Lower values trade off accuracy for speed.

  * `precision = 1e-3`: The threshold for early termination,

where precision is "roughly the fraction of true kNN allowed to be missed due to early termination". Lower values take longer but return more accurate results.
