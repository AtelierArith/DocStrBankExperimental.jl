```
Either{L, R} = Union{Const{L}, Identity{R}}
Either{Int, Bool}(true) == Identity(true)
Either{Int, Bool}(1) == Const(1)
Either{String}("left") == Const("left")
Either{String}(:anythingelse) == Identity(:anythingelse)
```

A very common type to represent Result or Failure. We reuse [`Identity`](@ref) as representing "Success" and [`Const`](@ref) for "Failure".
