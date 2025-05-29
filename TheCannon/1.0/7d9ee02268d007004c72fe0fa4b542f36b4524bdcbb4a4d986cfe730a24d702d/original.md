```
train(flux, ivar, labels, mask=nothing, verbose=true, quadratic=true)
```

returns: theta, scatters Run the training step of The Cannon, i.e. calculate coefficients for each pixel.

  * `flux` contains the spectra for each star in the training set.  It should be   `nstars x npixels` (row-vectors are spectra)
  * `ivar` contains the inverse variance for each pixel in the same shape as `flux`
  * `labels` contains the labels for each star.  It should be `nstars x nlabels`.  It will be expanded into the quadratic label space before training.
  * `mask` (optional) is a `nlabels x npix` matrix of booleans specifying which  labels are "allowed" to affect the spectrum at each pixel.

returns:

  * `theta`: the matrix containing the cannon coefficients.    It will be `n_expanded_labels x npix`
  * `scatters`: the model scatter at each pixel
