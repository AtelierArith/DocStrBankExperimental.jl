```
agc!(wav::Array, fs::Real=16000.0; maxvalue::Real=0.6, minstep::Real=-0.6)
```

Automatic gain control module for speech signals. The input signal `wav` would be changed after calling this function.

# Arguments

  * `wav`: raw speech signal
  * `fs`: sampling rate
  * `maxvalue`: specified maximum value for speech signal, maxvalue ∈ (0, +Inf)
  * `minstep`: minimum value to change the gain, minstep ∈ (-1, 0)
