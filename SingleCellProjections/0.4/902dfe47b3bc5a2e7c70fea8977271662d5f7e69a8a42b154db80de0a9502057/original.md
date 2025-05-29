```
pseudobulk(data::DataMatrix, obs_col, [additional_columns...]; var=:copy)
```

Create a new `DataMatrix` by averging over groups, as specified by the categorical annotation `obs_col` (and optionally additional columns).

  * `var` - Can be `:copy` (make a copy of source `var`) or `:keep` (share the source `var` object).

# Examples

Create a pseudobulk representation of each sample:

```julia
julia> pseudobulk(transformed, "sampleName")
```

Create a pseudobulk representation for each celltype in each sample:

```julia
julia> pseudobulk(transformed, "sampleName", "celltype")
```
