```
roundeven!(rop, op, rnd)
```

Set `rop` to `op` rounded to the nearest representable integer, rounding halfway cases with the even-rounding rule (like rint! with RNDN).

When `op` is a zero or an infinity, set `rop` to the same value with the same sign.
