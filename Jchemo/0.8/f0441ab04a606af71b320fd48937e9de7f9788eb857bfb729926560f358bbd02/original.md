```
recod_miss(X; miss = nothing)
recod_miss(df; miss = nothing)
```

Declare data as missing in a dataset.

  * `X` : A dataset (array).
  * `miss` : The code used in the dataset to identify the data    to be declared as `missing` (of type `Missing`).

Specific for dataframes:

  * `df` : A dataset (dataframe).

The case `miss = nothing` has the only action to allow `missing` in `X` or `df`. 

See examples.

## Examples

```julia
using Jchemo, DataFrames

X = hcat(1:5, [0, 0, 7., 10, 1.2])
X_miss = recod_miss(X; miss = 0)

df = DataFrame(i = 1:5, x = [0, 0, 7., 10, 1.2])
df_miss = recod_miss(df; miss = 0)

df = DataFrame(i = 1:5, x = ["0", "0", "c", "d", "e"])
df_miss = recod_miss(df; miss = "0")
```
