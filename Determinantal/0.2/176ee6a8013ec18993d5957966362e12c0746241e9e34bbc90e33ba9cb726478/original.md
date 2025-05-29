```
sample(L::AbstractLEnsemble,k)
```

Sample a k-DPP, i.e. a DPP with fixed size. k needs to be strictly smaller than the rank of L (if it equals the rank of L, use a ProjectionEnsemble).

The algorithm uses a saddle-point approximation adapted from Barthelmé, Amblard, Tremblay (2019).
