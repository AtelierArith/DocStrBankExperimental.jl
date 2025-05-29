```
MLJModelInterface.selectrows(::Model, I, data...) -> sampled_data
```

A model overloads `selectrows` whenever it buys into the optional `reformat` front-end for data preprocessing. See [`reformat`](@ref) for details. The fallback assumes `data` is a tuple and calls `selectrows(X, I)` for each `X` in `data`, returning the results in a new tuple of the same length. This call makes sense when `X` is a table, abstract vector or abstract matrix. In the last two cases, a new object and *not* a view is returned.
