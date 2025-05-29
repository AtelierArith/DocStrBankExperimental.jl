`calc_ccf_chunk!( ccf_out, chunk, ccf_plan )` Convenience function to compute CCF for one chunk of spectrum, evaluated using mask_shape and line list from ccf plan

# Inputs:

  * `ccf_out`:  `AbstractArray` to store output
  * `chunk`: ChunkOfSpectrum to compute CCF for
  * `ccf_plan`: for now, just a BasicCCFPlan that provides line*list, mask*shape and other parameters for calculating CCF

# Optional Arguments:

  * `assume_sorted`:  if true, skips checking the line_list is sorted by wavelength

# Returns:

  * `ccf_out`
