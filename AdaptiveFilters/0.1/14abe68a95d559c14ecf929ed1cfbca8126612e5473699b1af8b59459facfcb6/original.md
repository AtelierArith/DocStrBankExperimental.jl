```
focused_adaptive_filter(y, band, fs, args...; kwargs...)
```

An adaptive filter that focuses its attention to a specific frequency range.

#Arguments:

  * `y`: Input signal
  * `band`: Frequency band typle
  * `fs`: Sample rate, e.g., 44100
  * `args`: Passed through to `adaptive_filter`
  * `kwargs`: Passed through to `adaptive_filter`
