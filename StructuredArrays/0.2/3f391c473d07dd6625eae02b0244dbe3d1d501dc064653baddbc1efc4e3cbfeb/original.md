```
FastUniformArray(val, args...) -> A
FastUniformArray{T}(val, args...) -> A
FastUniformArray{T,N}(val, args...) -> A
FastUniformArray{T,N,val}(args...) -> A
```

build an immutable uniform array `A` whose elements are all equal to `val` and whose axes are specified by `args...`. The difference with an instance of [`UniformArray`](@ref) is that `val` is part of the type signature so that `val` can be known at compile time. A typical use is to create all true/false masks.
