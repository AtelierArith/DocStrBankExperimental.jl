```
pn = with_nominal(p, val)
```

Endow particles `p` with a nominal value `val`. The particle closest to `val` will be replaced with val, and moved to index 1. This operation introduces a slight bias in the statistics of `pn`, but the operation is asymptotically unbiased for large sample sizes. To obtain the nominal value of `pn`, call `nominal(pn)`.
