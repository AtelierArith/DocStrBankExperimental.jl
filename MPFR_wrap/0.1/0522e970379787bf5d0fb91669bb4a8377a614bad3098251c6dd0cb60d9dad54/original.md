```
beta!(rop, op1, op2, rnd)
```

Set `rop` to the value of the Beta function at arguments `op1` and `op2`. Note: the current code does not try to avoid internal overflow or underflow, and might use a huge internal precisionin some cases.
