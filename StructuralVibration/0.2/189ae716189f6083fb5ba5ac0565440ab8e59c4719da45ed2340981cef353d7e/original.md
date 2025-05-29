```
SineWave(F, tstart, duration, freq; zero_end = true)
```

Struct to define a sine wave excitation signal

**Constructor parameters**

  * `F::Real`: Amplitude of the force [N]
  * `tstart::Real`: Starting time of the excitation [s]
  * `duration::Real`: Duration of the excitation [s]
  * `freq::Real`: Frequency of the excitation [Hz]
  * `zero_end::Bool`: Boolean to set the excitation to 0 at the end of the duration (default = true)

**Fields**

  * `F::Real`: Amplitude of the force [N]
  * `tstart::Real`: Starting time of the excitation [s]
  * `duration::Real`: Duration of the excitation [s]
  * `ω::Real`: Frequency of the excitation [Hz]
  * `zero_end::Bool`: Boolean to set the excitation to 0 at the end of the duration (default = true)
