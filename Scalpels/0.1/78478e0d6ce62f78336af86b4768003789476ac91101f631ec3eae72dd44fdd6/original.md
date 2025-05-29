`calc_clean_rvs_scores_basis_scalpels(rvs, ccfs; σ_rvs, num_basis, sort_by_responce )` Computes cleaned rvs as well as the CCF basis functions and scores for a Scalpels reconstruction of CCFs Inputs:

  * rvs:  vector of estimated radial velocities
  * ccfs: 2d array of CCFS of size (num*velocities, num*spectra)

Optional Inputs:

  * σ_rvs:  vector of measurement uncertainties for estimated radial velocities (default: ones)
  * num_basis:  number of basis vectors to use for SVD reconstruction of CCFs
  * sort*by*responce:  set true to sort basis vectors by RV responce (default: true)

Output: (rvs, scores, basis): a NamedTuple

Notes:

  * Currently Scalpels weights all velocity pixels equally and uses the σ_rvs to weight each observation.
  * First element of output starts with RMS with zero basis vectors (i.e., the input RVs)
