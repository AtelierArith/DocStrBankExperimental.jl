```
lngamma!(rop, op, rnd)
```

Set `rop` to the value of the logarithm of the Gamma function on `op`, rounded in the direction `rnd`. When `op` is 1 or 2, set `rop` to +0 (in all rounding modes). When `op` is an infinity or a nonpositive integer, set `rop` to +Inf, following the general rules on special values. When `−2k−1<op<−2k`, `k` being a nonnegative integer, set `rop` to NaN.
