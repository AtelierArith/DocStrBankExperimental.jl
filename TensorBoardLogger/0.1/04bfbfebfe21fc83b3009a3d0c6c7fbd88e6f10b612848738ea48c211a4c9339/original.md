```
log_audio(logger::TBLogger, name::AbstractString, samples::AbstractArray, samplerate::Real; step=step(logger))
```

Logs an audio clip with name `name` at step `step`

  * samples: Array of samples N*C where N = number of samples and C = number of channels
  * samplerate: Sampling rate or Sampling frequency: a Real value
