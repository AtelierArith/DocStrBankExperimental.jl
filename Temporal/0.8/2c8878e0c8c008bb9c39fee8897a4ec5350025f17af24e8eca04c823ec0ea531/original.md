```
boy(x::TS; cal::Bool=false)
```

Return a time series containing all observations occuring at the beginnings of the years of the input.

  * If `cal` is `false`, only observations occurring the last calendar day of the year are returned
  * If `cal` is `true`, all observation for which the previous index is a prior year are returned
