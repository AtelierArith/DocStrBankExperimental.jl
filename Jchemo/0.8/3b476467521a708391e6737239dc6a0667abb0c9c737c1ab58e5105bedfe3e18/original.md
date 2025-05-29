```
convertdf(df::DataFrame; miss = nothing, typ)
```

Convert the columns of a dataframe to given types.

  * `df` : A dataframe.
  * `miss` : The code used in `df` to identify the data    to be declared as `missing` (of type `Missing`).   See function `recod_miss`.
  * `typ` : A vector of the targeted types for the   columns of the new dataframe.

## Examples

```julia
using Jchemo, DataFrames
```
