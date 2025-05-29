```
PinOrigin()
```

Projective transformation that translates the data so that the upper left bounding corner is at the origin `(0, 0)` (or the multidimensional equivalent).

Projective transformations on images return `OffsetArray`s, but not on keypoints. Hardware like GPUs do not support OffsetArrays, so they will be unwrapped and no longer match up with the keypoints.

Pinning the data to the origin makes sure that the resulting `OffsetArray` has the same indices as a regular array, starting at one.
