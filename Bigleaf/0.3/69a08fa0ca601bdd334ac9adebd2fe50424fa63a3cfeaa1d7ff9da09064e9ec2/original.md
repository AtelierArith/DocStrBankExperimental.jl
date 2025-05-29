```
setinvalid_afterprecip!(df; min_precip = 0.01, hours_after = 24.0)
```

Set records after precipitation to false in `:valid` column.

# Arguments

  * df: DataFrame with columns `:datetime` and `:precip` sorted by `:datetime`  in increasing order.

optional:

  * `min_precip` (in mm per timestep): minimum precip to be considered effective precipitation.
  * `hours_after`: time after the precipitation event to be considered invalid

# Value

`df` with modified column `:valid`.
