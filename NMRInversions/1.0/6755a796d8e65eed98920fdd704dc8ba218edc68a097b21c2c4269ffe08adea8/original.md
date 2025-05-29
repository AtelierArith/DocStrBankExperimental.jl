```
inv_out_1D(seq, x, y, xfit, yfit, X, f, r, SNR, α, selections, filter, title)
```

Output of the invert function for 1D pulse sequences. A structure containing the following fields:

  * `seq` is the 1D pulse sequence (e.g. IR, CPMG, PFG)
  * `x`, the x values of the measurement (e.g time for relaxation or b-factor for diffusion).
  * `y`, the y values of the measurement.
  * `xfit`, the x values of the fitted data.
  * `yfit`, the y values of the fitted data.
  * `X`, the x values of the inversion results.
  * `f`, the inversion results.
  * `r`, the residuals.
  * `SNR`, the signal-to-noise ratio.
  * `α`, the regularization parameter.
  * `selections`, a vector of tuples whose elements indicate the first and last index of the selected peaks.
  * `filter`, a vector representing the mask used to filter and scale the data.
  * `title`, a title describing the data.
