```
gaussian_noise(; kwargs...)
```

Synthesize bandpass Gaussian noise at a specified overall level

Synthesizes bandpass Gaussian noise by first selecting a random vector of numbers from the unit normal distribution and then filtering them with (by default) a 4th order Butterworth  bandpass filter from `freq_low` to `freq_high` (although any filter can be passed in its place via the `filter` argument, in which case `freq_low` and `freq_high` are ignored).

# Arguments:

  * `freq_low=0.5e3`: Lower cutoff of the bandpass filter (Hz)
  * `freq_high=20e3`: Upper cutoff of the bandpass filter (Hz)
  * `level=50.0`: Overall level before ramping (dB SPL)
  * `dur=1.0`: Total duration, including ramps (s)
  * `dur_ramp=0.01`: Ramp duration (s)
  * `fs=100e3`: Sampling rate (Hz)
  * `filter`: Filter used to bandpass filter noise (by default, 4th order Butterworth)
