```
approx(input::FunctionEvaluations, c::Convex, a::FullOrder)
```

Approximate using full order fitting that adds planes for all sample points.

This algorithm requires that the data points provided are samples from a convex function.
