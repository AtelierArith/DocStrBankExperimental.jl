```
abs!(rop, op, rnd)
```

Set `rop` to the absolute value of `op`, rounded in the direction `rnd`. Just changes or adjusts the sign if `rop` and `op` are the same variable, otherwise a rounding might occur if the precision of `rop` is less than that of `op`.
