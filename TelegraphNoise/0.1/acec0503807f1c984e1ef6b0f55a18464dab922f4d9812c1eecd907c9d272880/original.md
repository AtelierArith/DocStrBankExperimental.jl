```
generate_telegraph([rng = default_rng()], dwell_time, signal_length; amplitude = one(T) ) → Telegraph
```

Function that initializes a random [`Telegraph`](@ref) signal with a  specified `dwell_time` and of a given length `signal_length`.
