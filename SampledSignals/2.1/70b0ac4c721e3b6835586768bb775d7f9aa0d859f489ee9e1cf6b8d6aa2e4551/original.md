```
inHz(quantity[, rate])
```

Translate a particular quantity (usually a frequency) to a (unitless) value in Hz.

If the given quantity is Unitful, we use the given units. If it is not we assume it is already a value in Hz.

For some units (e.g. frames) you will need to specify a sample rate:

# Example

julia> inHz(1.0kHz) 1000.0
