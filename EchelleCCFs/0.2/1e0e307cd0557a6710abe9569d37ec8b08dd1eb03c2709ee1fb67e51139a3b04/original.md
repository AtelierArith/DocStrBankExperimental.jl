`calc_ccf_chunklist_timeseries( chunklist_timeseries, line_list )` Convenience function to compute CCF for a timeseries of spectra, each with a chunklist. Uses multiple threads if avaliable.

# Inputs:

  * chunklist_timeseries

# Optional Arguments:

  * ccf_plan (BasicCCFPlan())
  * verbose (false)

# Return:

CCF summed over all chunks in a spectrum's chunklist, evaluated using the ccf*plan. Note that the ccf*plan provided is used as a template for creating a custom ccf*plan for each chunk that     only includes lines that reliably appear in that order for all spectra in the chunklist*timeseries.
