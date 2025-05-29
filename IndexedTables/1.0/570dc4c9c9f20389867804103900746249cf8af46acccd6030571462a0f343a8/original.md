```
groupby(f, t, by = pkeynames(t); select, flatten=false, usekey = false)
```

Apply `f` to the `select`-ed columns (see [`select`](@ref)) in groups defined by the unique values of `by`.

If `f` returns a vector, split it into multiple columns with `flatten = true`.

To retain the grouping key in the resulting group use `usekey = true`.

# Examples

```
using Statistics

t=table([1,1,1,2,2,2], [1,1,2,2,1,1], [1,2,3,4,5,6], names=[:x,:y,:z])

groupby(mean, t, :x, select=:z)
groupby(identity, t, (:x, :y), select=:z)
groupby(mean, t, (:x, :y), select=:z)

groupby((mean, std, var), t, :y, select=:z)
groupby((q25=z->quantile(z, 0.25), q50=median, q75=z->quantile(z, 0.75)), t, :y, select=:z)

# apply different aggregation functions to different columns
groupby((ymean = :y => mean, zmean = :z => mean), t, :x)

# include the grouping key
groupby(t, by; usekey = true) do key, dd
    # code using key as key (named tuple) and dd as data
end
```
