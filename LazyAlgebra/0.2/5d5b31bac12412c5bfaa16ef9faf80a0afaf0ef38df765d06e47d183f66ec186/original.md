```julia
is_linear(A)
```

yields whether `A` is certainly a linear mapping.

!!! note
    This method is intended to perform certain automatic simplifications or optimizations.  It is guaranted to return `true` when its argument is certainly a linear mapping but it may return `false` even though its argument behaves linearly because it is not always possible to figure out that a complex mapping assemblage has this property.


See also: [`LinearType`](@ref).
