```
vcatdf(dat; cols = :intersect)
```

Vertical concatenation of a list of dataframes.

  * `dat` : List (vector) of dataframes.
  * `cols` : Determines the columns of the returned dataframe.   See ?DataFrames.vcat.

## Examples

```julia
using Jchemo, DataFrames

dat1 = DataFrame(rand(5, 2), [:v3, :v1]) 
dat2 = DataFrame(100 * rand(2, 2), [:v3, :v1])
dat = (dat1, dat2)
Jchemo.vcatdf(dat)

dat2 = DataFrame(100 * rand(2, 2), [:v1, :v3])
dat = (dat1, dat2)
Jchemo.vcatdf(dat)

dat2 = DataFrame(100 * rand(2, 3), [:v3, :v1, :a])
dat = (dat1, dat2)
Jchemo.vcatdf(dat)
Jchemo.vcatdf(dat; cols = :union)
```
