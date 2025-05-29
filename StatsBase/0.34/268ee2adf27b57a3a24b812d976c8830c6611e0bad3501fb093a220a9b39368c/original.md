```
indicatormat(x, c=sort(unique(x)); sparse=false)
```

Construct a boolean matrix `I` of size `(length(c), length(x))`. Let `ci` be the index of `x[i]` in `c`. Then `I[ci, i] = true` and all other elements are `false`.
