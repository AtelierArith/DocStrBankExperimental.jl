```
cond(x, y, z)
```

Return `y` if `x` is `true`, otherwise return `z`. If `x` is a vector, the operation is vectorized. This function mimics `x ? y : z`, which cannot be vectorized.
