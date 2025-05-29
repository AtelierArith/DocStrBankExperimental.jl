```
cost_matrix([C,] a, b) -> Matrix
```

Precompute the cost matrix given a cost function `C`. If no function `C` is provided, the default is `C(x,y) = norm(x-y)`.
