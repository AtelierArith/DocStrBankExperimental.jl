```julia
is_selfadjoint(A)
```

yields whether mapping `A` is certainly a self-adjoint linear mapping.

!!! note
    This method is intended to perform certain automatic simplifications or optimizations.  It is guaranted to return `true` when its argument is certainly a self-adjoint linear mapping but it may return `false` even though its argument behaves like a self-adjoint linear map because it is not always possible to figure out that a complex mapping construction has this property or because, for efficiency reasons, the coefficients of the mapping are not considered for this trait.


See also: [`SelfAdjointType`](@ref).
