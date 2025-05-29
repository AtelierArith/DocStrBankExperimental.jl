```
dim!(rop, op1, op2, rnd)
```

Set `rop` to the positive difference of `op1` and `op2`, i.e.,`op1−op2` rounded in the direction `rnd` if `op1>op2`, +0 if `op1≤op2`, and throws a DomainError if `op1` or `op2` is NaN.
