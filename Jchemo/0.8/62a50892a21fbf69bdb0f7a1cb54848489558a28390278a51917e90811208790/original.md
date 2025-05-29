```
dupl(X; digits = 3)
```

Find duplicated rows in a dataset.

  * `X` : A dataset.
  * `digits` : Nb. digits used to round `X` before checking.

## Examples

```julia
using Jchemo

X = rand(5, 3)
Z = vcat(X, X[1:3, :], X[1:1, :])
dupl(X)
dupl(Z)

M = hcat(X, fill(missing, 5))
Z = vcat(M, M[1:3, :])
dupl(M)
dupl(Z)
```
