```
Highs_getStringOptionValue(highs, option, value)
```

Get a string-valued option.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `option`: The name of the option.
  * `value`: A pointer to allocated memory (of at least `kMaximumStringLength`) to store the current value of the option.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
