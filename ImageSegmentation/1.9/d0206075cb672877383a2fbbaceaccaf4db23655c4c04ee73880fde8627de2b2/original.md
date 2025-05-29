```
segments = felzenszwalb(img, k, [min_size])
```

Segment an image using Felzenszwalb's segmentation algorithm and returns the result as `SegmentedImage`. The algorithm uses euclidean distance in color space as edge weights for the region adjacency graph.

Parameters:

  * `img`:      input image
  * `k`:        Threshold for region merging step. Larger threshold will result in bigger segments.
  * `min_size`: Minimum segment size (in # pixels)
