```
smote([rng=default_rng()], data::AbstractVecOrMat, n::Int; k::Union{Nothing,Int}=nothing)
smote([rng=default_rng()], data, n::Int; k::Union{Nothing,Int}=nothing)
```

Return the sample obtained via Synthetic Minority Over-sampling TEchnique (SMOTE) (Chawla et al., [2002](https://doi.org/10.1613/jair.953)) for

  * `data`: Data as a matrix or satisfying the tables interface.   For matices, each column denotes a point and for tables each row denotes a point.
  * `n`: Number of synthetic points that should be created.
  * `k`: Number of nearest neighbors to consider for each point.

For each minority class, the algorithm creates synthetic points along the lines in between one of the `k` nearest neighbors. The location of the point along the line is chosen randomly.

The implementation is based on the pseudocode from the paper, but do note that the paper has a weird API (especially `N`) and the implementation is full of indexing logic. The essence is much simpler than the pseudocode: To find `n` new points, take a random point `p` for each `n` from the minority group and for each `p` take a random point along the line to the nearest neighbor.
