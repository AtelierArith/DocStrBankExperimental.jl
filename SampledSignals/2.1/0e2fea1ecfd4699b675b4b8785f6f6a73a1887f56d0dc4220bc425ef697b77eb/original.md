```
inframes([Type,]quantity[, rate])
```

Translate the given quantity to a (unitless) number of time or frequency frames, given a particular samplerate. Note that this isn't quantized to integer numbers of frames. If given a `Type`, the result will first be coerced to the given type.

If the given quantity is Unitful, we use the given units. If it is not we assume it is already a value in frames.

# Example

julia> inframes(0.5s, 44100Hz) 22050.0

julia> inframes(1000Hz, 2048/44100Hz) 46.439909297052154
