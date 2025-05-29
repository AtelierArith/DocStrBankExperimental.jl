```
summ(X; digits = 3)
summ(X, y; digits = 3)
```

Summarize a dataset (or a variable).

  * `X` : A dataset (n, p).
  * `y` : A categorical variable (n) (class membership).
  * `digits` : Nb. digits in the outputs.

## Examples

```julia
using Jchemo

n = 50
X = rand(n, 3) 
y = rand(1:3, n)
res = summ(X)
@names res
summ(X[:, 2]).res

summ(X, y)
```
