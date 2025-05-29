```
var_counts_sum([f=identity], counts::DataMatrix, filter, col; check=true, var=:keep, obs=:keep)
```

For each observation, compute the sum of counts matching the `filter`.

If `f` is specified, it is applied to each element before summing. (Similar to `sum`.)

kwargs:

  * `var` - Use this to set `var` in the `ProjectionModel`.
  * `obs` - Use this to set `obs` in the `ProjectionModel`. Note that `counts.obs` is changed in place, regardless of the value of `obs`.

If `check=true`, an error will be thrown if no variables match the pattern.

For more information on filtering syntax, see examples below and the documentation on [`DataFrames.filter`](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter).

# Examples

Sum all "Gene Expression" counts:

```
var_counts_sum(counts, "feature_type"=>isequal("Gene Expression"), "totalRNACount")
```

Compute the number of "Gene Expression" variables that are expressed (i.e. nonzero):

```
var_counts_sum(!iszero, counts, "feature_type"=>isequal("Gene Expression"), "nonzeroRNACount")
```

See also: [`var_counts_sum!`](@ref)
