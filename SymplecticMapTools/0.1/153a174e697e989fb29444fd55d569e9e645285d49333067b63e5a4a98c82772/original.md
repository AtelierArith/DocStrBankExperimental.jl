```
wba_weight(d, N)
```

Weights used in the weighted Birkhoff average, returned as a diagonal matrix. Returns as `Diagonal([w_1, ..., w_1, ..., w_N, ..., w_N])`, where each coefficient is repeated `d` times (this is used for vector MPE and RRE as a least-squares weighting)
