```
mask = flood(src, idx, nbrhood_function=diamond_iterator((3,3,...)); thresh)
```

Return an array `mask` with the same axes as `src`, marked `true` for all connected elements of `src` for which `src[i]` has a Euclidean distance less than `thresh` from `src[idx]`.
