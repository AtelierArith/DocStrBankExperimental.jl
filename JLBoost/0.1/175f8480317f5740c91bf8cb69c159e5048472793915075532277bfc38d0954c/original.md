```
find_best_split(loss, feature, target, warmstart, lambda, gamma)
```

Find the best (binary) split point by optimizing ∑ loss(warmstart + δx, target) using order-2 Taylor series expexpansion.

Does not assume that Feature, target, and warmstart are sorted and will sort them for you.
