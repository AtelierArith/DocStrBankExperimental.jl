```
rowgap!(gl::GridLayout, i::Integer, s::Union{Fixed, Relative, Real})
rowgap!(gl::GridLayout, s::Union{Fixed, Relative, Real})
```

Set the gap between rows in `gl`.  The two-argument version sets all row gaps in `gl`.  The three-argument version sets the gap between rows `i` and `i+1`. Passing a real number to `s` has the same behaviour as passing `Fixed(s)`.

See also [Fixed](@ref) and [Relative](@ref).
