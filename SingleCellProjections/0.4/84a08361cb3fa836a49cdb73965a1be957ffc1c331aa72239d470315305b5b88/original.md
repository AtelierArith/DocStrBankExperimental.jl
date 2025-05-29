```
var_counts_fraction(counts::DataMatrix, sub_filter, tot_filter, col; check=true, var=:copy, obs=:copy)
```

For each observation, compute the fraction of counts that match a specific variable pattern.

  * `sub_filter` decides which variables are counted.
  * `tot_filter` decides which variables to include in the total.

kwargs:

  * `var` - Can be `:copy` (make a copy of source `var`) or `:keep` (share the source `var` object).
  * `obs` - Can be `:copy` (make a copy of source `obs`) or `:keep` (share the source `obs` object).

If `check=true`, an error will be thrown if no variables match the patterns.

For more information on filtering syntax, see examples below and the documentation on [`DataFrames.filter`](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter).

# Examples

Compute the fraction of reads in MT- genes, considering only "Gene Expression" features (and not e.g. "Antibody Capture").

```
var_counts_fraction(counts, "name"=>startswith("MT-"), "feature_type"=>isequal("Gene Expression"), "fraction_mt")
```

Compute the fraction of reads in MT- genes, when there is no `feature_type` annotation (i.e. all variables are genes).

```
var_counts_fraction(counts, "name"=>startswith("MT-"), Returns(true), "fraction_mt")
```

See also: [`var_counts_fraction!`](@ref)
