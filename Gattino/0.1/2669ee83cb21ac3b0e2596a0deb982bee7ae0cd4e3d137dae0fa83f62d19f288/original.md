```julia
group(f::Function, c::AbstractContext, w::Int64 = c.dim[1],
    h::Int64 = c.dim[2], margin::Pair{Int64, Int64} = c.margin) -> ::Nothing
```

Creates a *scaling group* on `c`, the `Context` (or `Group`). This will *not* create  a layer, only a scaling window. This creates the `Group` in the same way, but draws its children to  `c`'s children. For layers, use `group!`

```example

```
