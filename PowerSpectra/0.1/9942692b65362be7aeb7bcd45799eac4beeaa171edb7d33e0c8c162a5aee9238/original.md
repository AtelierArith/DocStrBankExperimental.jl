```
coupledcov(ch1, ch2, workspace, spectra;
           noiseratios=Dict(), lmax=0) where T
```

# Arguments:

  * `ch1::Symbol`: spectrum type of first spectrum (i.e. :TT, :TE, :EE)
  * `ch2::Symbol`: spectrum type of second spectrum (i.e. :TT, :TE, :EE)
  * `workspace`: cache for working with covariances
  * `spectra`: signal spectra

# Keywords

  * `noiseratios::AbstractDict`: ratio of noise spectra to white noise
  * `lmax=0`: maximum multipole moment for covariance matrix

# Returns:

  * `SpectralArray{T,2}`: covariance matrix (0-indexed)
