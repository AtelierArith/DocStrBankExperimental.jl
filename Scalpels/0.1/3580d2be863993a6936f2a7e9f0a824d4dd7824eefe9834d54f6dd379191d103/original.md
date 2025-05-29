`clean_rvs_scalpels(rvs, ccfs; σ_rvs, num_basis )` Inputs:

  * rvs:  vector of estimated radial velocities
  * ccfs: 2d array of CCFS of size (num*velocities, num*spectra)

Optional Inputs:

  * σ_rvs:  vector of measurement uncertainties for estimated radial velocities (default: ones)
  * num_basis:  number of basis vectors to use for SVD reconstruction of CCFs
  * sort*by*responce:  set true to sort basis vectors by RV responce (default: true)

Output: rvs_clean: vector of estimated RVs after cleaning by scalpels

Notes:

  * Currently Scalpels weights all observations equally and doesn't use the σ_rvs.
  * First element of output starts with RMS with zero basis vectors (i.e., the input RVs)
