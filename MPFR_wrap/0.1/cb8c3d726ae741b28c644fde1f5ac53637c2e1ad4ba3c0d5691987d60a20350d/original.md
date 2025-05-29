```
floor!(rop, op, rnd)
```

Set `rop` to `op` rounded to the next lower or equal representable integer (like rint! with RNDD).

When `op` is a zero or an infinity, set `rop` to the same value with the same sign.
