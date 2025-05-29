```
evaluate_flow_error(ground_truth_flow, estimated_flow, AngularError())
```

Returns a 2-Dimensional array that matches the dimensions of the input flow vector and that depicts the angle error between the estimated flow and the ground truth flow.

# Details

If the estimated flow at a point is (u0, v0) and ground truth flow is (u1, v1), it calculates the angle between (u0, v0, 1) and (u1, v1, 1) vectors as measure for error.

# Arguments

The flow parameters needs to be two-dimensional arrays of length-2 vectors (of type SVector) which represent the displacement of each pixel.

# Example

Compute the angle error between two flows.

```julia

using ImageTracking

result = evaluate_flow_error(ground_truth_flow, estimated_flow, AngularError())

imshow(result)
```

# References

[1] S. Baker, D. Scharstein, JP Lewis, S. Roth, M.J. Black, and R. Szeliski. A database and evaluation methodology for optical flow. International Journal of Computer Vision, 92(1):1–31, 2011.
