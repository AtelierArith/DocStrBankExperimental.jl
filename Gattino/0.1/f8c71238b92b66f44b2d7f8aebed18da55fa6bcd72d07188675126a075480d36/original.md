```julia
group!(f::Function, c::AbstractContext, name::String, w::Int64 = c.dim[1],
    h::Int64 = c.dim[2], margin::Pair{Int64, Int64} = c.margin) -> ::Nothing
```

Creates a layer by name `name` on `c`, and scales that layer to the dimensions provided.

```example

```
