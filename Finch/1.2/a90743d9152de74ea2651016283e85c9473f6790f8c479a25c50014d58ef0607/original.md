```
bandmask
```

A mask for a banded tensor, `bandmask[i, j, k] = j <= i <= k`. Note that this specializes each column for the cases where `i < j`, `j <= i <= k`, and `k < i`.
