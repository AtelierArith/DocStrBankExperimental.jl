```
log_audios(logger::TBLogger, name::AbstractString, samples::AbstractArray, samplerate::Real; step=step(logger))
```

Logs multiple audio clips at step `step`

  * samples:   Array of audio clips which are Arrays of samples N*C where N = number of samples and C = number of channel
  * samplerate: Sampling rate or Sampling frequency: a Real value same for all clips
