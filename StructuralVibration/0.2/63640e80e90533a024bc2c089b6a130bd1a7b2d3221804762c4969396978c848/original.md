```
SweptSine(F, tstart, duration, fstart, fend, type)
```

Struct to define a swept sine excitation signal

**Fields**

  * `F::Real`: Amplitude of the force [N]
  * `tstart::Real`: Starting time of the excitation [s]
  * `duration::Real`: Duration of the excitation [s]
  * `fstart::Real`: Starting frequency [Hz]
  * `fend::Real`: Ending frequency [Hz]
  * `type::Symbol`: Type of sweep

      * `:lin` - linear (default)
      * `:quad` - quadratic
      * `:log` - logarithmic
  * `zero_end::Bool`: Boolean to set the excitation to 0 at the end of the duration (default = true)
