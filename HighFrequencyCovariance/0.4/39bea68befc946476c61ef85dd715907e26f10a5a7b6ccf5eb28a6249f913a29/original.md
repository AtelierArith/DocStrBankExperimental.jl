```
get_returns(dd::DataFrame; rescale_for_duration::Bool = false)
```

Converts a long format `DataFrame` of prices into a `DataFrame` of returns.

### Inputs

  * `dd` - A `DataFrame` with a column called :Time and all other columns being asset prices in each period.
  * `rescale_for_duration` - Should returns be rescaled to reflect a common time interval.

### Returns

  * A `DataFrame` of returns.
