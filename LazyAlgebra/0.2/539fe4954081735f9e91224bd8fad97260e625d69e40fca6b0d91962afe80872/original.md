```julia
is_diagonal(A)
```

yields whether mapping `A` is certainly a diagonal linear map.

!!! note
    This method is intended to perform certain automatic simplifications or optimizations.  It is guaranted to return `true` when its argument is certainly a diagonal linear map but it may return `false` even though its argument behaves like a diagonal linear map because it is not always possible to figure out that a complex mapping assemblage has this property.


See also: [`DiagonalType`](@ref).
