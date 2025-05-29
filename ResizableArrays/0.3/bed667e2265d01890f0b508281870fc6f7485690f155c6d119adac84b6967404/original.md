```
grow!(A, B, prepend=false) -> A
```

grows resizable array `A` with the elements of `B` and returns `A`. If `prepend` is `true`, the elements of `B` are inserted before those of `A`; otherwise, the elements of `B` are appended after those of `A`. By default, `prepend` is `false`.

Assuming `A` has `N` dimensions, array `B` may have `N` or `N-1` dimensions. The `N-1` leading dimensions of `A` and `B` must be identical and are the leading dimensions of the result. If `B` has the same number of dimensions as `A`, the last dimension of the result is the sum of the last dimensions of `A` and `B`; otherwise, the last dimension of the result is one plus the last dimension of `A`.

Depending on argument `prepend`, calling the `grow!` method is equivalent to calling `append!` or `prepend!` methods.

See also [`ResizableArray`](@ref).
