```
indices(x::Stencil, I::Union{Tuple,CartesianIndex})
indices(x::AbstractStencilArray, I::Union{Tuple,CartesianIndex})
```

Returns an `SVector` of `CartesianIndices` for each neighbor around `I`.

`indices` for `Stencil` do not know about array boundaries and wil not wrap or reflect. On `AbstractStencilArray` they will wrap and reflect depending on the boundary condition  of the array.
