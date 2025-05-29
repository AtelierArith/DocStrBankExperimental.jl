```
inHz(quantity)
```

Translate a particular quantity (usually a frequency) to a (unitless) value in Hz.

If the given quantity is Unitful, we use the given units. If it is not we assume it is already a value in Hz.

## Examples

```jldoctest
julia> inHz(1.0kHz)
1000.0
```
