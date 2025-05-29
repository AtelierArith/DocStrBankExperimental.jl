```
get_nonoverlapping_periods(dfo::DataFrame)
```

Get non-overlapping periods.

# Arguments

  * `dfo`: DataFrame with columns `p_start` and `p_end` sorted by increasing `p_start`

# Value

  * DataFrame with columns `p_start` and `p_end` with `p_start[i] > p_end[i-1]`
