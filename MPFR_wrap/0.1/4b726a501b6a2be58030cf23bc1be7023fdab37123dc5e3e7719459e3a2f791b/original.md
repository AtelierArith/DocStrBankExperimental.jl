```
gamma_inc!(rop, op, op2, rnd)
```

Set `rop` to the incomplete Gamma function on `op1` and `op2`, rounded in the direction `rnd`. (In the literature, `gamma_inc` is called upper incomplete Gamma function, or sometimes complementary incomplete Gamma function.) For `gamma_inc`, when `op2` is zero and `op` is a negative integer, `rop` is set to NaN.

Note: the current implementation of `gamma_inc` is slow for large values of `rop` or `op`, in which case some internal overflow might also occur.
