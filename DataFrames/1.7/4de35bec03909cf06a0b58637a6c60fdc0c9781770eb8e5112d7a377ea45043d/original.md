```
isapprox(df1::AbstractDataFrame, df2::AbstractDataFrame;
         rtol::Real=atol>0 ? 0 : √eps, atol::Real=0,
         nans::Bool=false, norm::Function=norm)
```

Inexact equality comparison. `df1` and `df2` must have the same size and column names. Return  `true` if `isapprox` with given keyword arguments applied to all pairs of columns stored in `df1` and `df2` returns `true`.
