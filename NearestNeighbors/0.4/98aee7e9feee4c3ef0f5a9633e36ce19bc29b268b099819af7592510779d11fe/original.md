```
inrange!(idxs, tree, point, radius)
```

Same functionality as `inrange` but stores the results in the input vector `idxs`. Useful if one want to avoid allocations or specify the element type of the output vector.

See also: `inrange`, `inrangecount`.
