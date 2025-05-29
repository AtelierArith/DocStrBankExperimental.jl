```
calculate_statistics(error)
```

Quantifies the flow error in terms of a mean and standard deviation as well as two additional statistics that measure "robustness".

# Details

RX and AX are the robustness statistics. RX denotes the percentage of pixels that have an error measure over X. AX denotes the accuracy of the error measure at the Xth percentile.

# Arguements

The error parameters needs to be two-dimensional arrays of length-2 vectors (of type SVector) which represent the error between two flows.

# Example

Compute the Mean, SD, RX, AX stats of the flow error calculated using endpoint error method.

```julia

using ImageTracking

error = evaluate_flow_error(ground_truth_flow, estimated_flow, EndpointError())
mean, sd, rx, ax = calculate_statistics(error)
```

Compute the mean, SD, RX, AX stats of the flow error calculated using angula error method.

```julia

using ImageTracking

error = evaluate_flow_error(ground_truth_flow, estimated_flow, AngularError())
mean, sd, rx, ax = calculate_statistics(error)
```

# References

[1] S. Baker, D. Scharstein, JP Lewis, S. Roth, M.J. Black, and R. Szeliski. A database and evaluation methodology for optical flow. International Journal of Computer Vision, 92(1):1–31, 2011.
