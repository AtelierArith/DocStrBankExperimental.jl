```
vzero!(x) -> x
```

fills `x` with zeros and returns it.  The default implementation just calls `fill!(x,zero(eltype(x)))` but this method may be specialized for specific types of variables `x`.

Also see [`vfill!`](@ref).
