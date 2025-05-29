```
flow, indicator  = optical_flow(source, target, points, LucasKanade(Args...))
flow, indicator  = optical_flow(source, target, points, displacement, LucasKanade(Args...))
```

Returns the optical flow from the `source` to the `target` image for the specified `points` using the `LucasKanade` algorithm.

# Details

The `source` and `target` images must be `Gray` types.

The `points` argument is of type `Array{SVector{2, Float64}, 2}` and represents a set of keypoints in the `source` image for which the optical flow is to be computed. The coordinates  of a `point` represent the  `(row, column)` of a pixel in the image. The `displacement` argument allows you to specify an initial guess for the optical flow.

The function returns `flow` of type `Array{SVector{2, Float64}, 2}` which matches the length of `points` and represents the displacement needed to map a point in the `source` image to the `target` image.

The `indicator` is a vector of boolean values (one for each point in `points`) which signals whether a particular point was successfully tracked or not.

In order to use the `flow` to index the corresponding point in the `target` image you first need to round it to the nearest integer, and check that it falls within the bounds of the `target` image dimensions.
