```
approx(input::FunctionEvaluations, c::Convex, a::Progressive)
```

Approximate using a progressive fitting heuristic that adds planes until a specified error tolerance is met.

This algorithm requires that the data points provided are samples from a convex function.
