```
frac!(rop, op, rnd)
```

Set `rop` to the fractional part of `op`, having the same sign as `op`, rounded in the direction `rnd` (unlike in rint!, `rnd` affects only how the exact fractional part is rounded, not how the fractional part is generated). When `op` is an integer or an infinity, set `rop` to zero with the same sign as `op`.
