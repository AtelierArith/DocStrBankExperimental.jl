```
cosm(X)
cosm(X, Y)
```

Compute a cosinus matrix.

  * `X` : Data (n, p).
  * `Y` : Data (n, q).

The function computes the cosinus matrix: 

  * of the columns of `X`:  ==> (p, p) matrix
  * or between columns of `X` and `Y` :  ==> (p, q) matrix.

## Examples

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)
Y = rand(n, 3)

cosm(X)
cosm(X, Y)
```
