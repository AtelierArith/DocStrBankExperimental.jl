```
ColoredNoise(F, color)
```

Struct to define a colored noise excitation signal

**Fields**

  * `F::Real`: Mean amplitude of the force [N]
  * `tstart::Real`: Starting time of the excitation [s]
  * `duration::Real`: Duration of the excitation [s]
  * `σ::Real`: Target standard deviation of the colored noise
  * `color::Symbol`: Color of the noise

      * `:white` (default)
      * `:pink`
      * `:blue`
      * `:brown`
      * `:purple`
  * `band_freq::AbstractVector`: Frequencies used to defined the bandpass filter applied to the colored noise
