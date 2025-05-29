```
load_counts([loadfun=load10x], filenames;
            sample_names,
            sample_name_col,
            obs_id_col = "cell_id",
            lazy,
            lazy_merge = false,
            obs_id_delim = '_',
            obs_id_prefixes = sample_names,
            extra_var_id_cols::Union{Nothing,String,Vector{String}},
            duplicate_var,
            duplicate_obs,
            callback=nothing)
```

Load and merge multiple samples efficiently.

Defaults to loading 10x CellRanger files. The files are first loaded lazily, then the merged count matrix is allocated and finally each sample is loaded directly into the merged count matrix. (This strategy greatly reduces memory usage, since only one copy of data is needed instead of two.)

`filenames` specifies which files to load. (It can be a vector of filenames or a single filename string.) For each file, `loadfun` is called.

  * `sample_names` - Specify the sample names. Should be a vector of the same length as `filenames`. Set to `nothing` to not create a sample name annotation.
  * `sample_name_col` - Column for sample names in `obs`, defaults to "sampleName".
  * `obs_id_col` - Colum for merged `id`s in `obs`.
  * `lazy` - Enable lazy loading. Defaults to true if `load10x` is used, and `false` otherwise.
  * `lazy_merge` - Enable lazy merging, i.e. `var` and `obs` are created, but the count matrix merging is postponed until a second call to `load_counts`.
  * `obs_id_delim` - Delimiter used when creating merged `obs` IDs.
  * `obs_id_prefixes` - Prefix (one per sample) used to create new IDs. Set to nothing to keep old IDs. Defaults to `sample_names`.
  * `extra_var_id_cols` - Additional columns to use to ensure variable IDs are unique during merging. Defaults to "feature_type" if that column is present for all samples. Can be a `Vector{String}` to include multiple columns. Set to nothing to disable.
  * `duplicate_var` - Set to `:ignore`, `:warn` or `:error` to decide what happens if duplicate var IDs are found.
  * `duplicate_obs` - Set to `:ignore`, `:warn` or `:error` to decide what happens if duplicate obs IDs are found.
  * `callback` - Experimental callback functionality. The callback function is called between samples during merging. Return `true` to abort loading and `false` to continue.
  * Additional kwargs (including `duplicate_var`/`duplicate_obs` if specified) are passed to `loadfun`.

# Examples

Load and name samples:

```julia
julia> counts = load_counts(["s1.h5", "s2.h5"]; sample_names=["Sample A", "Sample B"])
```

See also: [`load10x`](@ref), [`merge_counts`](@ref)
