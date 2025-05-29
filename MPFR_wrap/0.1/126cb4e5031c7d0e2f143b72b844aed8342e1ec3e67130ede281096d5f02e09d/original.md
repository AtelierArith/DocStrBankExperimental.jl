```
rec_sqrt!(rop, op, rnd)
```

Set `rop` to 1/√op rounded in the direction `rnd`. Set `rop` to +Inf if op is ±0,+0 if `op` is +Inf, and throw a DomainError exception if `op` is negative. Warning!  Therefore the result on −0 is different from the one of the `sqrt` function recommended by the IEEE 754-2008 standard (Section 9.2.1), which is −Inf instead of +Inf.
