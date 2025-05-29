```julia
is_endomorphism(A)
```

yields whether mapping `A` is certainly an endomorphism.

!!! note
    This method is intended to perform certain automatic simplifications or optimizations.  It is guaranted to return `true` when its argument is certainly an endomorphism but it may return `false` even though its argument behaves like an endomorphism because it is not always possible to figure out that a complex mapping assemblage has this property.


See also: [`MorphismType`](@ref).
