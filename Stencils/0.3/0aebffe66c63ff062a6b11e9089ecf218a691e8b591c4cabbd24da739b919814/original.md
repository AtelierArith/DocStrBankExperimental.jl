```
stencil(A::AbstractStencilArray)
stencil(A::AbstractStencilArray, I...)
```

Get a [`Stencil`](@ref) with neighbors updated for indices `I`.

`I` can be a `CartesianIndex`, a `Tuple`, or splatted arguments.

Without passing `I`, the stencil will not be updated, and will likely contain `nothing` values - but it may still be useful for its other methods.
