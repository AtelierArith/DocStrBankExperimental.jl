```
setagc(;gain=1.0, maxvalue=0.6, minstep=-0.6)
```

Set the automatic-gain-control module's parameters.

# Optional Arguments

  * `gain`: inital speech signal's gain value
  * `maxvalue`: specified maximum value for speech signal, maxvalue ∈ (0, +Inf)
  * `minstep`: minimum value to change the gain, minstep ∈ (-1, 0)
