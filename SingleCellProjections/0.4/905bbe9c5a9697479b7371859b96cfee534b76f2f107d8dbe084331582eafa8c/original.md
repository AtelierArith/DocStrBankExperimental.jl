```
merge_counts(samples, sample_names;
             lazy=false,
             sample_name_col = sample_names===nothing ? nothing : "sampleName",
             obs_id_col = "cell_id",
             obs_id_delim = '_',
             obs_id_prefixes = sample_names,
             extra_var_id_cols::Union{Nothing,String,Vector{String}},
             duplicate_var,
             duplicate_obs,
             callback=nothing)
```

Merge `samples` to create one large DataMatrix, by concatenating the `obs`. The union of the variables from the samples is used, and if a variable is not present in a sample, the count will be set to zero.

The `obs` IDs are created by concatenating the current `obs` ID columns, together with the `sample_names` (if provided).

  * `lazy` - Lazy merging. Use `load_counts` to actually perform the merging.
  * `sample_name_col` - Column in which the `sample_names` are stored.
  * `obs_id_col` - Name of `obs` ID column after merging. (Set to nothing to keep old column name.)
  * `obs_id_delim` - Delimiter used when merging `obs` IDs.
  * `obs_id_prefixes` - Prefix (one per sample) used to create new IDs. Set to nothing to keep old IDs. Defaults to `sample_names`.
  * `extra_var_id_cols` - Additional columns to use to ensure variable IDs are unique during merging. Defaults to "feature_type" if that column is present for all samples. Can be a `Vector{String}` to include multiple columns. Set to nothing to disable.
  * `duplicate_var` - Set to `:ignore`, `:warn` or `:error` to decide what happens if duplicate var IDs are found.
  * `duplicate_obs` - Set to `:ignore`, `:warn` or `:error` to decide what happens if duplicate obs IDs are found.
  * `callback` - Experimental callback functionality. The callback function is called between samples during merging. Return `true` to abort loading and `false` to continue.

See also: [`load_counts`](@ref)
