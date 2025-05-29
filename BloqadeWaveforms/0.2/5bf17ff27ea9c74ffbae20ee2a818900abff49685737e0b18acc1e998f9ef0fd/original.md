```
sinusoidal(;duration::Real, amplitude::Real=one(start))
```

Create a sinusoidal waveform of the following expression.

```julia
amplitude * sin(2π*t)
```

# Keyword Arguments

  * `duration`: duration of the waveform.
  * `amplitude`: amplitude of the sin waveform.
