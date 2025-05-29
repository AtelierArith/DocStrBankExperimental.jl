```
HelmertCoding([base[, levels]])
HelmertCoding(; base=nothing, levels=nothing)
```

Helmert coding codes each level as the difference from the average of the lower levels.

If `levels` are omitted or `nothing`, they are determined from the data by calling the `levels` function when constructing `Contrastsmatrix`.  If `base` is omitted or `nothing`, the first level is used as the base. For each non-base level, Helmert coding generates a columns with -1 for each of n levels below, n for that level, and 0 above.

When all levels are equally frequent, Helmert coding generates columns that are mean-centered (mean 0) and orthogonal.

# Examples

```julia
julia> StatsModels.ContrastsMatrix(HelmertCoding(), ["a", "b", "c", "d"]).matrix
4×3 Array{Float64,2}:
 -1.0  -1.0  -1.0
  1.0  -1.0  -1.0
  0.0   2.0  -1.0
  0.0   0.0   3.0
```
