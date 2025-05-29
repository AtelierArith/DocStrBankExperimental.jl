```
ContrastResult{T,M,R,C} <: AbstractMatrix{T}
```

Matrix type that holds least-square weights obtained from one or more [`RegDIDResultOrAgg`](@ref)s computed over the same set of cells and cell-level averages. See also [`contrast`](@ref).

The least-square weights are stored in a `Matrix` that can be retrieved with property name `:m`, where the weights for each treatment coefficient are stored columnwise starting from the second column and the first column contains the cell-level averages of outcome variable. The indices for cells can be accessed with property name `:r`; and indices for identifying the coefficients can be accessed with property name `:c`. The [`RegDIDResultOrAgg`](@ref)s used to generate the `ContrastResult` can be accessed by calling `parent`.
