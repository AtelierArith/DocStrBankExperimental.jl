Perform overall baseline correction using ALS and centered Moving Average.

  * `stim_frame=0`: Disables stimulus-based normalization.
  * `ma_tail_start=0`: Disables ignored region in the moving average correction.
  * `window`: Size of the moving average window.

Returns a baseline-corrected dF/F trace.
