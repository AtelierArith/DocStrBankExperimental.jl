```
fma(rop, op1, op2, op3, rnd)
```

Set `rop` to `(op1×op2)+op3` rounded in the direction `rnd`. Concerning special values (signed zeros, infinities, NaN), these functions behave like a multiplication followed by a separate addition or subtraction. That is, the fused operation matters only for rounding.
