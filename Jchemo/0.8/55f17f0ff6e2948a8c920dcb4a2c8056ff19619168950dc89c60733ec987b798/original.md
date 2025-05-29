```
tab(X::AbstractArray)
tab(X::DataFrame; vary = nothing)
```

Tabulation of categorical variables.

  * `x` : Categorical variable or dataset containing categorical variable(s).

Specific for a dataset:

  * `vary` : Vector of the names of the group variables to consider    in `X` (by default: all the columns of `X`).

The output cointains sorted levels.

## Examples

```julia
using Jchemo, DataFrames

x = rand(["a"; "b"; "c"], 20)
res = tab(x)
res.keys
res.vals

n = 20
X = hcat(rand(1:2, n), rand(["a", "b", "c"], n))
df = DataFrame(X, [:v1, :v2])

tab(X[:, 2])
tab(string.(X))

tab(df)
tab(df; vary = [:v1, :v2])
tab(df; vary = :v2)
```
