```
trunc!(rop, op, rnd)
```

Set `rop` to `op` rounded to the next representable integer toward zero (like rint! with RNDZ).

When `op` is a zero or an infinity, set `rop` to the same value with the same sign.
