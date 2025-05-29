```
get_significant_roi_pixels(analysis::ROIAnalysis, data::Experiment{TWO_PHOTON}; channel_idx::Int=1)
```

Get the pixel coordinates for all significant ROIs in the original image.

Parameters:

  * `analysis`: The ROIAnalysis object containing processed ROI data
  * `data`: The original Experiment object containing the ROI mask
  * `channel_idx`: Channel index to use for determining significant ROIs (default: 1)

Returns:

  * Vector of linear indices for pixels in significant ROIs from the specified channel
