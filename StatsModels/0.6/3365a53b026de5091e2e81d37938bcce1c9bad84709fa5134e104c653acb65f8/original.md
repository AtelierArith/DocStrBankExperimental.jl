```
DummyCoding([base[, levels]])
DummyCoding(; base=nothing, levels=nothing)
```

Dummy coding generates one indicator column (1 or 0) for each non-base level.

If `levels` are omitted or `nothing`, they are determined from the data by calling the `levels` function on the data when constructing `ContrastsMatrix`. If `base` is omitted or `nothing`, the first level is used as the base.

Columns have non-zero mean and are collinear with an intercept column (and lower-order columns for interactions) but are orthogonal to each other. In a regression model, dummy coding leads to an intercept that is the mean of the dependent variable for base level.

Also known as "treatment coding" or "one-hot encoding".

# Examples

```julia
julia> StatsModels.ContrastsMatrix(DummyCoding(), ["a", "b", "c", "d"]).matrix
4×3 Array{Float64,2}:
 0.0  0.0  0.0
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0
```
