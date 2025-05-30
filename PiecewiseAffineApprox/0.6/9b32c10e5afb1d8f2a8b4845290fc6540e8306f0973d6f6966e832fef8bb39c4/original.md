```
approx(input::FunctionEvaluations, c::Convex, a::Cluster)
```

Approximate using a heuristic that works for general dimensions.

Additional keyword arguments:

  * `trials`: number of restarts (default = 20)
  * `itlim`: max refining iterations in each trial (default = 50),
