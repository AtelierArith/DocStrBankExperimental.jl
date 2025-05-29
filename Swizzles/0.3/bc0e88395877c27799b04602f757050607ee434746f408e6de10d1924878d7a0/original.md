```
swizzle(v, indices...)
swizzle(T, v, indices...)
```

Create a new object made up of `v[i₁], v[i₂], ...` where `indices = (i₁, i₂, ...)`. If a type is provided as first argument, the result will be wrapped into it via [`construct_swizzle`](@ref).

A default type is derived from `swizzle(v, indices...)`, where a single index infers `T = eltype(v)`, and multiple indices infer `T = typeof(v)`. For statically sized vectors (`StaticVector` and `SizedVector`), an extension extends [StaticArraysCore](https://github.com/JuliaArrays/StaticArraysCore.jl) vectors such that one of correct size is used to hold the result.

See also: [`swizzle!`](@ref)
