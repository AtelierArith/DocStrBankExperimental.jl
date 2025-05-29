```
eow(x::TS; cal::Bool=false)
```

Return a time series containing all observations occuring at the ends of the weeks of the input.

  * If `cal` is `false`, only observations occurring the last calendar day of the week are returned
  * If `cal` is `true`, all observation for which the next index is a new week are returned
