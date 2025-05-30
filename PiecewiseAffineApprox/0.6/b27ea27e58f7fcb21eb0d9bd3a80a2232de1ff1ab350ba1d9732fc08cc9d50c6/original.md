```
enforce_curvature(f::FunctionEvaluations, curvature::Curvature, optimizer, metric = :l1)
```

Create a slightly perturbed version of the function values to ensure that the data points can be interpolated by a convex/concave piecewise affine function.

Enforcing the curvature is performed using a linear optimization problem that adjust the function values and tries to minimize the total deviation. The total deviation can be measured in different metrics specified by the `metric` parameter. This function can be useful as a pre-step for running the full-order and progressive fitting heuristics that require data points that are convex/concave in this sense.
