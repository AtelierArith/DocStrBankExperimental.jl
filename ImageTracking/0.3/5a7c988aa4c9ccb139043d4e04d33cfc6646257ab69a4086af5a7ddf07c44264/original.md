```
flow = optical_flow(source, target, Farneback(Args...))
flow = optical_flow(source, target, displacement, Farneback(Args...))
```

Returns the dense optical flow from the `source` to the `target` image using the `Farneback` algorithm.

# Details

The `source` and `target` images must be `Gray` types.

The `displacement` argument allows you to specify an initial guess for the optical flow and must be of type `Array{SVector{2, Float64}, 2}`. The elements of `displacement` should represent the flow required to map the `(row, column)` of each pixel in the `source` image to the `target` image.
