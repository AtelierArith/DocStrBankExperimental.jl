```
attribute(X, ptr::Union{Ptr,CuPtr}, attr)
```

Returns attribute `attr` about pointer `ptr`. The type of the returned value depends on the attribute, and as such must be passed as the `X` parameter.
