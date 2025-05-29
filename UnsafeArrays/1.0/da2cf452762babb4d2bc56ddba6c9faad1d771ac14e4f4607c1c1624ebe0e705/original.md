```
uview(A::AbstractArray, I...)
```

Unsafe equivalent of `view`. May return an `UnsafeArray`, a standard `SubArray` or `A` itself, depending on `I...` and the type of `A`.

As `uview` may return an `UnsafeArray`, `A` itself and it's contents *must* be protected from garbage collection (e.g. via `GC.@preserve` on Julia > v0.6) and memory reallocation while the view is in use.

Use `uviews(f::Function, As::AbstractArray...)` or `@uviews A ... expr` to use unsafe views of one or multiple arrays with automatically GC protection.

```
uviews(A, B, ...) do (A_u, B_u, ...)
    # Do something with the unsafe views A_u, B_u, ...
    # Code here must not resize/append/etc. A, B, ...
end
```

To provide support for `uview` for custom array types, add methods to function `UnsafeArrays.unsafe_uview`.
