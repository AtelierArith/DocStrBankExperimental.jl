```
Highs_getDoubleOptionValues(highs, option, current_value, min_value, max_value, default_value)
```

Get the current and default values of a double option

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `current_value`: A pointer to the current value of the option.
  * `min_value`: A pointer to the minimum value of the option.
  * `max_value`: A pointer to the maximum value of the option.
  * `default_value`: A pointer to the default value of the option.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
