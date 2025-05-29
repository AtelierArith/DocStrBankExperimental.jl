```
aggstat(X, y; algo = mean)
aggstat(X::DataFrame; varx, vary, algo = mean)
```

Compute column-wise statistics by class in a dataset.

  * `X` : Data (n, p).
  * `y` : A categorical variable (n) (class membership).
  * `algo` : Function to compute (default = mean).

Specific for dataframes:

  * `varx` : Names (vector) of the variables to summarize.
  * `vary` : Names (vector) of the the categorical variables to consider   for computations by class.

Variables defined in `varx` and `vary` must be columns of `X`.

## Examples

```julia
using Jchemo, DataFrames, Statistics

n, p = 20, 5
X = rand(n, p)
df = DataFrame(X, :auto)
y = rand(1:3, n)
res = aggstat(X, y; algo = sum)
@names res
res.lev 
res.X
aggstat(df, y; algo = sum).X

n, p = 20, 5
X = rand(n, p)
df = DataFrame(X, string.("v", 1:p))
df.y1 = rand(1:2, n)
df.y2 = rand(["a", "b", "c"], n)
df
aggstat(df; varx = [:v1, :v2], vary = [:y1, :y2], algo = var)  # return a dataframe 
```
