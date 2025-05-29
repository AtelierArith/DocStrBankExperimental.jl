```
NegativeDistanceHack(dist)
```

Evaluates as the negative of the distance function being wrapped. This is not a real distance function but a simple hack to get a similarity and use it for searching for farthest elements (farthest points / farthest pairs) on indexes that can handle this hack (e.g., `ExhaustiveSearch`, `ParallelExhaustiveSearch`, `SearchGraph`).
