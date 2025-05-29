```
vfill!(x, α) -> x
```

sets all elements of `x` with the scalar value `α` and return `x`.  The default implementation just calls `fill!(x,α)` but this method may be specialized for specific types of variables `x`.

Also see [`vzero!`](@ref), [`fill!`](@ref).
