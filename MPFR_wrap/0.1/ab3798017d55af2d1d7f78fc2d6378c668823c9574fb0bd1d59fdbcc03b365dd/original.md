```
cmp_2exp(op1, op2, e)
```

Compare `op1` and `op2 × 2^e`: returns a positive value if `op1>op2 × 2^e`, zero if `op1=op2 × 2^e` or a negative number if `op1<op2 × 2^e`. Throws an exception if `op1` is NaN.
