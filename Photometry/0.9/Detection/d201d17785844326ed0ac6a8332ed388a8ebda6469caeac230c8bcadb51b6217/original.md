```
PeakMesh(box_size=(3, 3), nsigma=3.0)
```

Detect sources by finding peaks above a threshold in grids across the image.

This creates a pixel-wise threshold for sources by calculating `error * nsigma` when used with [`extract_sources`](@ref). The peaks are found by searching the image in boxes of size `box_size`. If the maximum value in that box is greater than the threshold set above, the point is extracted.
