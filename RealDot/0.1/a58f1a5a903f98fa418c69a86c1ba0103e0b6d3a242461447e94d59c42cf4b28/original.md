```
realdot(x, y)
```

Compute `real(dot(x, y))` while avoiding computing the imaginary part if possible.

This function can be useful if you work with derivatives of functions on complex numbers. In particular, this computation shows up in pullbacks for non-holomorphic functions.
