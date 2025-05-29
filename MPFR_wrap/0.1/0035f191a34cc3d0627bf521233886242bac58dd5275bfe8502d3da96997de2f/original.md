```
sqrt!(rop, op, rnd)
```

Set `rop` to `√op` rounded in the direction `rnd`. Set `rop` to −0 if `op` is −0, to be consistent with the IEEE 754 standard. Throw a DomainError exception if `op` is negative.
