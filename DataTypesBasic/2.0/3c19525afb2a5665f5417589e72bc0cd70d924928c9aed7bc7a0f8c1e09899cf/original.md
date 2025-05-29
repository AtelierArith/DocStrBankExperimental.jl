```
Option{T} = Union{Const{Nothing}, Identity{T}}
Option(nothing) == Const(nothing)
Option("anything but nothing") == Identity("anything but nothing")
Option() == Const(nothing)
```

Like `Union{T, Nothing}`, however with container semantics. While `Union{T, Nothing}` can be thought of like a value which either exists or not, `Option{T} = Union{Identity{T}, Const{Nothing}}` is a container which is either empty or has exactly one element.

We reuse [`Identity`](@ref) as representing the single-element-container and `Const(nothing)` as the empty container.
