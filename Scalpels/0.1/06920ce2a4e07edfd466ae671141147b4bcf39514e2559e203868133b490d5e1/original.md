`rms_clean_rvs_vs_num_basis_scalpels(rvs, ccfs; σ_rvs, max_num_basis )` Compute RMS of estimated RVs after cleaning raw RVS with Scalpels algorithm (based on CCFs)

Inputs:

  * rvs:  vector of estimated radial velocities
  * ccfs: 2d array of CCFS of size (num*velocities, num*spectra)

Optional Inputs:

  * σ_rvs:  vector of measurement uncertainties for estimated radial velocities (default: ones)
  * max*num*basis:  maximum number of basis vectors to use for SVD reconstruction of CCFs
  * sort*by*responce:  set true to sort basis vectors by RV responce (default: true)

Output: rms_scalpels: vector of RMS estimated RVs after cleaning by scalpels as a function of the number of basis vectors

Notes:

  * Currently Scalpels weights all observations equally and doesn't use the σ_rvs.
  * First element of output starts with RMS with zero basis vectors (i.e., the input RVs)
