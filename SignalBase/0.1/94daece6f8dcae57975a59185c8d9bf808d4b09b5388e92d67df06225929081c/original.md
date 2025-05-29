```
inseconds(quantity[, rate])
```

Translate a particular quantity (usually a time) to a (unitless) value in seconds.

If the given quantity is Unitful, we use the given units. If it is not we assume it is already a value in seconds.

For some units (e.g. frames) you will need to specify a frame rate. If not specified the rate is `missing`.

## Examples

```jldoctest
julia> inseconds(50.0ms)
0.05

julia> inseconds(441frames, 44100Hz)
0.01
```
