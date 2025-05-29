`calc_ccf_and_var_chunk!( chunk, ccf_plan )` Convenience function to compute CCF and variance of each "CCF pixel" for one chunk of spectrum, evaluated using mask*shape and line list from `ccf*plan`.

# Inputs:

  * `ccf_out`:  `AbstractArray` to store output
  * `ccf_var_out`:  `AbstractArray` to store output
  * `chunk`: ChunkOfSpectrum to compute CCF for
  * `ccf_plan`: for now, just a BasicCCFPlan that provides line*list, mask*shape and other parameters for calculating CCF

# Optional Arguments:

  * `var`:  `AbstractArray` with variance to use for each pixel (overides value in chunk)
  * `assume_sorted`:  if true, skips checking the line_list is sorted by wavelength

# Returns Named Tuple with:

  * `ccf_out`:
  * `ccf_var_out`:
