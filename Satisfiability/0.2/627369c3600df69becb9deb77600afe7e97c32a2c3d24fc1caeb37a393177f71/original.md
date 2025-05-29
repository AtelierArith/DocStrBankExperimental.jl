```
bvcomp(a, b)
bvcomp(a, bvconst(a, 0xffff, 16))
```

Bitwise comparator: iff all bits of `a` and `b` are equal, `bvcomp(a,b) = 0b1`, otherwise `0b0`.
