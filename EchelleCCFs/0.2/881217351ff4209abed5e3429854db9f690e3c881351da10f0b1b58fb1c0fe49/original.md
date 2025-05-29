`calc_ccf_and_var_chunklist ( chunklist, ccf_plans )` Convenience function to compute CCF based on a spectrum's chunklist.

# Inputs:

  * chunklist
  * vector of ccf plans (one for each chunk)

# Optional Arguments:

  * `assume_sorted`:  if true, skips checking the line_list is sorted by wavelength

# Return:

CCF summed over all chunks in a spectrum's chunklist, evaluated using the line list and mask_shape from the ccf plan for each chunk.
