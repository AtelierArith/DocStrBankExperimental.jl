```
round!(rop, op, rnd)
```

Set `rop` to `op` rounded to the nearest representable integer, rounding halfway cases away from zero (as in the roundTiesToAway mode of IEEE 754-2008).

When `op` is a zero or an infinity, set `rop` to the same value with the same sign.
