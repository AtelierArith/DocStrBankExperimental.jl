```
process_rois(data::Experiment{TWO_PHOTON, T}; 
    stim_indices=nothing,
    channels=nothing,
    roi_indices=nothing,
    delay_time=50.0,
    window::Int=15,
    n_stds=2.0,
    sig_window=50.0,  # Time window in ms to look for significant responses after stimulus
    kwargs...
) where T<:Real
```

Process regions of interest (ROIs) from two-photon imaging data with the following steps:

1. Split pixels into ROIs if not already done (use pixel*splits*roi!)
2. For each ROI and channel:

      * Extract ROI traces
      * Calculate baseline using pre-stimulus period
      * Compute dF/F using moving average correction
      * Fit parametric model to response
      * Calculate significance based on threshold within specified time window

Returns:     ROIAnalysis object containing processed data for each ROI
