```
arg(L::Line, z)
```

Find a parameter argument `t` such that `L(t)==z` is true. For an infinite `z`, return zero (but note that `L(1)` is also infinity).

This gives undefined results if `z` is not actually on the line.
