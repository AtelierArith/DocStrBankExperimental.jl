```
mvreplace(x, y)
```

Return `y` if `x` is `missing`, otherwise return `x`. If `x` is a vector, the operation is vectorized. This function mimics `x ? y : z`, which cannot be vectorized.
