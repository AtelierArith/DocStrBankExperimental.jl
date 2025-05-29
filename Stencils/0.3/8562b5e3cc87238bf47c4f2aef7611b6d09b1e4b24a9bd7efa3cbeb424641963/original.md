```
Layered <: Abstract

Layered(layers::Union{Stencil,Layered}...)
Layered(; layer_keywords...)
Layered(layers::Union{Tuple,NamedTuple})
```

`Tuple` or `NamedTuple` of stencils that can be used together.

`neighbors` for `Layered` returns a tuple of iterators for each stencil layer.
