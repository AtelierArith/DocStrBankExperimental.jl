```
deg(a::AbstractLinear)
```

Return `deg(x)` where `x` is the first term appearing in `a` (as determined by `first(a)`).

The linear combination `a` must not be zero. If `a` is homogeneous, then `deg(a)` is the common degree of all terms in it.
