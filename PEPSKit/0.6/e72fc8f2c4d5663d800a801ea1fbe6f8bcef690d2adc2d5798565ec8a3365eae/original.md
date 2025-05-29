```
expectation_value(pf::InfinitePartitionFunction, inds => O, env::CTMRGEnv)
```

Compute the expectation value corresponding to inserting a local tensor(s) `O` at position `inds` in the partition function `pf` and contracting the chole using a given CTMRG environment `env`.

Here `inds` can be specified as either a `Tuple{Int,Int}` or a `CartesianIndex{2}`, and `O` should be a rank-4 tensor conforming to the [`PartitionFunctionTensor`](@ref) indexing convention.
