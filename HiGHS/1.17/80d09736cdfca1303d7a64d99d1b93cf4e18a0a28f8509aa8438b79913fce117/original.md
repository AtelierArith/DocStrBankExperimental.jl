```
Highs_getOptionType(highs, option, type)
```

Get the type expected by an option.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `option`: The name of the option.
  * `type`: An int in which the corresponding `kHighsOptionType` constant should be placed.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
