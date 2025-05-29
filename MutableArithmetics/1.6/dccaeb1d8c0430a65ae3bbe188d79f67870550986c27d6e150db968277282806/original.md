```
copy_if_mutable(x)
```

Return a copy of `x` that can be mutated with MultableArithmetics's API without altering `x`. If `mutability(x)` is `IsNotMutable` then `x` is returned as none of `x` can be mutated. Otherwise, it redirects to [`mutable_copy`](@ref). Mutable types should not implement a method for this function but should implement a method for [`mutable_copy`](@ref) instead.
