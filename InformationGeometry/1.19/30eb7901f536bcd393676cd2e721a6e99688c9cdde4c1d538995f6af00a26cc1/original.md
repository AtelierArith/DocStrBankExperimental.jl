The `CompositeDataSet` type is a more elaborate (and typically less performant) container for storing data. Essentially, it splits observed data which has multiple `y`-components into separate data containers (e.g. of type `DataSet`), each of which corresponds to one of the components of the `y`-data. Crucially, each of the smaller data containers still shares the same "kind" of `x`-data, that is, the same `xdim`, units and so on, although they do **not** need to share the exact same particular `x`-data.

The main advantage of this approach is that it can be applied when there are `missing` `y`-components in some observations. A typical use case for `CompositeDataSet`s are time series where multiple quantities are tracked but not every quantity is necessarily recorded at each time step. Example:

```julia
using DataFrames
t = [1,2,3,4]
y₁ = [2.5, 6, missing, 9];      y₂ = [missing, 5, 3.1, 1.4]
σ₁ = 0.3*ones(4);               σ₂ = [missing, 0.2, 0.1, 0.5]
df = DataFrame([t y₁ σ₁ y₂ σ₂], :auto)

xdim = 1;   ydim = 2
CompositeDataSet(df, xdim, ydim; xerrs=false, stripedYs=true)
```

The boolean-valued keywords `stripedXs` and `stripedYs` can be used to indicate to the constructor whether the values and corresponding $1\sigma$ uncertainties are given in alternating order, or whether the initial block of `ydim` many columns are the values and the second `ydim` many columns are the corresponding uncertainties. Also, `xerrs=true` can be used to indicate that the `x`-values also carry uncertainties. Basically all functions which can be called on other data containers such as `DataSet` have been specialized to also work with `CompositeDataSet`s.
