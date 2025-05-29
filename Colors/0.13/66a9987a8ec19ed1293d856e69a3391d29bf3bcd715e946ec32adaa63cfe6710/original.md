```
DE_CMC(kl=1, kc=1)
```

Construct a metric using the CMC equation (CMC l:c), with weighting parameters `kl` and `kc`. When not provided, these parameters default to `1`.

!!! note
    The `DE_CMC` is a quasimetric, i.e. violates symmetry. Therefore, `colordiff(a, b, metric=DE_CMC())` may not equal to `colordiff(b, a, metric=DE_CMC())`. The first argument of `colordiff` is taken as the reference (standard) color.

