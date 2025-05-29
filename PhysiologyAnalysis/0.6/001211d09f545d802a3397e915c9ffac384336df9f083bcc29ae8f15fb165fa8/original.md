```
ROIAnalysis
```

Contains all ROI analysis results for a two-photon imaging experiment.

Fields:

  * `rois`: Dictionary mapping ROI ID to vector of ROITrace objects (one per stimulus per channel)
  * `stimulus_indices`: Vector of analyzed stimulus indices
  * `channels`: Vector of analyzed channel indices
  * `analysis_parameters`: Dictionary of analysis parameters (window size, delay time, etc.)
