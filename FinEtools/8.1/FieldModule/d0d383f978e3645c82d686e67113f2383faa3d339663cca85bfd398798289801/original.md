```
scattersysvec!(self::F, vec::AbstractVector{T}, kind::KIND_INT = DOF_KIND_FREE) where {F<:AbstractField,T<:Number}
```

Scatter values to the field from a system vector.

The vector may be for an arbitrary kind of degrees of freedom (default is the free degrees of freedom).
