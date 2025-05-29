```
SimilarityFromDistance(dist)
```

Evaluates as $1/(1 + d)$ for a distance evaluation $d$ of `dist`. This is not a distance function and is part of the hacks to get a similarity  for searching farthest elements on indexes that can handle this hack (e.g., `ExhaustiveSearch`, `ParallelExhaustiveSearch`, `SearchGraph`).
