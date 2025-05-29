```
mul!(rop, op1, op2, rnd)
```

Set `rop` to `op1×op2` rounded in the direction `rnd`. When a result is zero, its sign is the product of the signs of the operands (for types having no signed zeros, 0 is considered positive).
