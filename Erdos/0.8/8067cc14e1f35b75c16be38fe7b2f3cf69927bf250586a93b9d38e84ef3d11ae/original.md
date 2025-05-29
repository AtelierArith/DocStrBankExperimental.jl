```
minimum_cut(g, distmx=weights(g))
```

Return a tuple `(parity, bestcut)`, where `parity` is a vector of integer values that determines the partition in `g` (1 or 2) and `bestcut` is the weight of the cut that makes this partition. An optional `distmx` matrix may be specified; if omitted, edge distances are assumed to be 1.
