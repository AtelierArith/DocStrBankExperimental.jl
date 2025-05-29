```
datasetinfo(datasetpath; onlywithlabels = [], shufflelabels = [], rng = Random.GLOBAL_RNG)
```

Show dataset size on disk and return a Touple with first element a vector of selected IDs, second element the labels DataFrame or nothing and third element the total size in bytes.

# Arguments

  * `onlywithlabels` is used to select which portion of the Dataset to load, by specifying   labels and their values to use as filters. See [`loaddataset`](@ref) for more info.
  * `shufflelabels` is an `AbstractVector` of names of labels to shuffle (default = [], means   no shuffle).
  * `rng` is a random number generator to be used when shuffling (for reproducibility); can be   either a `Integer` (used as seed for `MersenneTwister`) or an `AbstractRNG`.
