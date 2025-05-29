```
euclsq(X, Y)
```

Squared Euclidean distances between the rows of `X` and `Y`.

  * `X` : Data (n, p).
  * `Y` : Data (m, p).

For `X`(n, p) and `Y` (m, p), the function returns  an object (n, m) with:

  * i, j = distance between row i of `X` and row j of `Y`.

## Examples

```julia
X = rand(5, 3)
Y = rand(2, 3)

euclsq(X, Y)

euclsq(X[1:1, :], Y[1:1, :])

euclsq(X[:, 1], 4)
euclsq(1, 4)
```
