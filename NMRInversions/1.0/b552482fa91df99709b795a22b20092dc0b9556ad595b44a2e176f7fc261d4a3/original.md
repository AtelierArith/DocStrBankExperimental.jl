```
input1D(seq, x, y)
```

A structure containing the following fields:

  * `seq` is the 1D pulse sequence (e.g. IR, CPMG, PFG)
  * `x`, the x values of the measurement (e.g time for relaxation or b-factor for diffusion).
  * `y`, the y values of the measurement.

It can be used as an input for the invert and expfit functions.
