```
rowsize!(gl::GridLayout, i::Integer, s::Union{Aspect, Auto, Fixed, Relative, Real})
```

Set the size of the `i`th row in `gl`, i.e., `gl[i, :]`. Passing a real number to `s` has the same behaviour as passing `Fixed(s)`.

See also [Aspect](@ref), [Auto](@ref), [Fixed](@ref), and [Relative](@ref).
