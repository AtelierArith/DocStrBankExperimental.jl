```
describe(md; t = fill([(1, 0, 0)], nmodalities(md)), kwargs...)
```

Return descriptive statistics for an `AbstractMultiDataset` as a `Vector` of new `DataFrame`s where each row represents a variable and each column a summary statistic.

# Arguments

  * `md`: the `AbstractMultiDataset`;
  * `t`: is a vector of `nmodalities` elements,   where each element is a vector as long as the dimensionality of

```
the i-th modality. Each element of the innermost vector is a tuple
of arguments for [`paa`](@ref).
```

For other see the documentation of [`DataFrames.describe`](@ref) function.

# Examples

TODO: examples
