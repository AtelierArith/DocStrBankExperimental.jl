```
inv_out_2D(seq, X_dir, X_indir, F, r, SNR, α, filter, selections)
```

Output of the invert function for 2D pulse sequences. A structure containing the following fields:

  * `seq` is the 2D pulse sequence (e.g. IRCPMG)
  * `X_dir`, the x values of the direct dimension.
  * `X_indir`, the x values of the indirect dimension.
  * `F`, the inversion results as a matrix.
  * `r`, the residuals.
  * `SNR`, the signal-to-noise ratio.
  * `alpha`, the regularization parameter.
  * `filter`, apply a mask to filter out artefacts when plotting.
  * `selections`, the selection masks (e.g. when you want to highlight some peaks in a T₁-T₂ map).
  * `title`, a title describing the data.
