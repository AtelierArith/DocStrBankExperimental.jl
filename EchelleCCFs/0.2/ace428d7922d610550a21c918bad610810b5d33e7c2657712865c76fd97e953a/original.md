`calc_ccf_chunk( chunk, ccf_plan )` Convenience function to compute CCF for one chunk of spectrum.

# Inputs:

  * `ccf_out`:  `AbstractArray` to store output
  * `chunk`: ChunkOfSpectrum to compute CCF for
  * `ccf_plan`: for now, just a BasicCCFPlan that provides line*list, mask*shape and other parameters for calculating CCF

# Optional Arguments:

  * `assume_sorted`:  if true, skips checking the line_list is sorted by wavelength
  * `calc_ccf_var`:  if true also computes estimate of variance for each value of ccf

# Returns:

  * CCF for one chunk of spectrum, evaluated using mask_shape and line list from ccf plan
