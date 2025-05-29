```
findmiss(X)
```

Find rows with missing data in a dataset.

  * `X` : A dataset.

For dataframes, see also `DataFrames.completecases` and `DataFrames.dropmissing`.

## Examples

```julia
using Jchemo

X = rand(5, 4)
zX = hcat(rand(2, 3), fill(missing, 2))
Z = vcat(X, zX)
findmiss(X)
findmiss(Z)
```
