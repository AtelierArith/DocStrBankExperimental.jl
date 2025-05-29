infer(flux, ivar, theta, scatters; quadratic=true, verbose=true)

Run the test step of the cannon.  Given `theta` and `scatters` (from training), infer stellar parameters.

  * `flux` contains the spectra for each star for which you want to infer labels

in the training set.  It should be `nstars x npixels` (row-vectors are spectra)

  * `ivar` contains the inverse variance for each pixel in the same shape as `flux`
  * `theta`: the matrix containing the cannon coefficients.  It will be `n_expanded_labels x npix`
  * `scatters`: the model scatter at each pixel

If `verbose` is set to true, gives an update for every 100 stars processed.
