```
Q = get_qm(pedlist)
Q = get_qm(T, pedlist)
```

Computes the Q-matrix relating unknown parent groups (UPG) to individuals, as suggested by Quaas (1988). The pedigree list `pedlist` should include a UPG code that is greater than the maximum ID of real animals. The type of `Q` is `T` (Float64 by default).
