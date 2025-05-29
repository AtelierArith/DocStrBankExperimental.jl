```
evaluate_flow_error(ground_truth_flow, estimated_flow, EndpointError())
```

Returns a 2-Dimensional array that matches the dimensions of the input flow vector and that depicts the end point error between the estimated flow and the ground truth flow.

# Details

If the estimated flow at a point is (u0, v0) and ground truth flow is (u1, v1), then error will be sqrt[(u0 - u1)^2 + (v0 - v1)^2] at that point.

# Arguments

The flow parameters needs to be two-dimensional arrays of length-2 vectors (of type SVector) which represent the displacement of each pixel.

# Example

Compute the end point error between two flows.

```julia

using ImageTracking

result = evaluate_flow_error(ground_truth_flow, estimated_flow, EndpointError())

imshow(result)
```

# References

[1] S. Baker, D. Scharstein, JP Lewis, S. Roth, M.J. Black, and R. Szeliski. A database and evaluation methodology for optical flow. International Journal of Computer Vision, 92(1):1–31, 2011.
