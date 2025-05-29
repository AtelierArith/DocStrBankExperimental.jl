```
CIEDE2000 <: SemiMetric
ciede2000(x, y; metric=DE_2000())
```

The pixel-wise `CIEDE2000` color-difference between image `a` and `b`. Optionally, a metric may be supplied, chosen among `DE_2000` (the default), `DE_94`, `DE_JPC79`, `DE_CMC`, `DE_BFD`, `DE_AB`, `DE_DIN99`, `DE_DIN99d`, `DE_DIN99o`.

## References

Sharma, G., Wu, W., and Dalal, E. N., 2005. *The CIEDE2000 color‐difference formula*.
