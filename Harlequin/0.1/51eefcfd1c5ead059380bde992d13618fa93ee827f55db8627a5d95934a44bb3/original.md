```
update_nobs_matrix!(nobs_matrix::Vector{NobsMatrixElement{T}}, psi_angle, sigma_squared, pixidx, flagged)
```

Apply Eq. (10) of KurkiSuonio2009 iteratively on the samples of a TOD to update matrices $M_p$ in `nobs_matrix`. The meaning of the parameters is the following:

  * `nobs_matrix` is the structure that gets updated by this function
  * `psi_angle` is an array of `N` elements, containing the polarization angles (in radians)
  * `sigma_squared` is an array of `N` elements, each containing the value of σ^2 for the samples in the TOD
  * `pixidx` is an array of `N` elements, containing the pixel index observed by the TOD
  * `flagged` is a Boolean array of `N` elements; `true` means that the sample in the TOD should not be used to produce the map. This can be used to produce jackknives and to neglect moving objects in the TOD
