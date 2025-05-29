```
sub!(rop, op1, op2, rnd)
```

Set `rop` to `op1-op2` rounded in the direction `rnd`. The IEEE 754 rules are used for signed zeros.

For types having no signed zeros, 0 is considered unsigned, i.e., `(+0)−0 = (+0)`, `(−0)−0 = (−0)`, `0−(+0) = (−0)` and `0−(−0) = (+0))`.
