```
constant_term(a)
```

Return the constant value (zero order coefficient) for `Taylor1` and `TaylorN`. The fallback behavior is to return `a` itself if `a::Number`, or `a[1]` when `a::Vector`.
