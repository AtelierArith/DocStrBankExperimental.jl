```
inframes([Type,]quantity[, rate])
```

Translate the given quantity to a (unitless) number of time frames, given a particular framerate. Note that this isn't quantized to integer numbers of frames. If given a `Type`, the result will first be coerced to the given type.

If the given quantity is Unitful, we use the given units. If it is not we assume it is already a value in frames.

For some units (e.g. frames) you will need to specify a frame rate. If not specified the rate is `missing`.

# Example

```jldoctest
julia> inframes(0.5s, 44100Hz)
22050.0

julia> inframes(Int,10.5frames)
10
```
