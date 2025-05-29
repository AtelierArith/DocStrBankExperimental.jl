```
rootn!(rop, op, k, rnd)
```

Set `rop` to the kth root of `op` rounded in the direction `rnd`. For k=0, set `rop` to NaN. For k odd (resp. even) and `op` negative (including −Inf), set `rop` to a negative number (resp. throw a DomainError). If `op` is zero, set `rop` to zero with the sign obtained by the usual limit rules, i.e., the same sign as `op` if `k` is odd, and positive if `k` is even.

This function agrees with the `rootn` function of the IEEE 754-2008 standard (Section 9.2).
