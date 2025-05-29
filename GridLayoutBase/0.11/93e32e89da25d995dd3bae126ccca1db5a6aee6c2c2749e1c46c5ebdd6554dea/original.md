```
colgap!(gl::GridLayout, i::Integer, s::Union{Fixed, Relative, Real})
colgap!(gl::GridLayout, s::Union{Fixed, Relative, Real})
```

Set the gap between columns in `gl`.  The two-argument version sets all column gaps in `gl`.  The three-argument version sets the gap between columns `i` and `i+1`. Passing a real number to `s` has the same behaviour as passing `Fixed(s)`.

See also [Fixed](@ref) and [Relative](@ref).
