```
eom(x::TS; cal::Bool=false)
```

Return a time series containing all observations occuring at the ends of the months of the input.

  * If `cal` is `false`, only observations occurring the last calendar day of the month are returned
  * If `cal` is `true`, all observation for which the next index is a new month are returned
