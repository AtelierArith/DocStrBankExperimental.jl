```
aggmean(X, y)
```

Compute column-wise mean by class in a dataset.

  * `X` : Data (n, p).
  * `y` : A categorical variable (n) (class membership).

Faster than `aggstat`. 

## Examples

```julia
using Jchemo

n, p = 20, 5
X = rand(n, p)
y = rand(1:3, n)
df = DataFrame(X, :auto) 
res = aggmean(X, y)
res.X
res.lev 
aggmean(df, y).X
```
