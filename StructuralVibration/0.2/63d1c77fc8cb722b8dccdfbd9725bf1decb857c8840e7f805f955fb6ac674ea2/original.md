```
SmoothRect(F, tstart, tr, duration)
```

Struct to define a smooth rectangular excitation signal

**Fields**

  * `F::Real`: Amplitude of the force [N]
  * `tstart::Real`: Starting time of the excitation [s]
  * `duration::Real`: Duration of the excitation [s]
  * `trise::Real`: Rise time from 0 to F [s]

*Note: `SmoothRect` is actually a custom Tukey window for which the coefficient α is computed to satisfy the `trise` given by the user*
