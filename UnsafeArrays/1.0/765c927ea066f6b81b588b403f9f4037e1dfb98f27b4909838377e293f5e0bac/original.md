```
uviews(f::Function, As::AbstractArray...)
```

Equivalent to `f(map(uview, As)...)`. Automatically protects the array(s) `As` from garbage collection during execution of `f`.

Example:

```
uviews(A, B, ...) do (A_u, B_u, ...)
    # Do something with the unsafe views A_u, B_u, ...
    # Code here must not resize/append/etc. A, B, ...
end
```

In many cases, it may be preferable to use `@uviews` insted of `views`.
