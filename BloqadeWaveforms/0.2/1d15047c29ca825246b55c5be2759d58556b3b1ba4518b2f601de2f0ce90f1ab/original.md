```
struct Waveform{F,T<:Real}
```

Type for waveforms. `Waveform`s are defined as a function combined with a real number duration.

# Fields

  * `f`: a callable object.
  * `duration`: a real number defines the duration of this waveform; default unit is `μs`.
