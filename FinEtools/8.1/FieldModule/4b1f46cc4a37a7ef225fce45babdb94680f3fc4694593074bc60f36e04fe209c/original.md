```
gathersysvec!(self::F, vec::Vector{T}, kind::KIND_INT = DOF_KIND_FREE) where {F<:AbstractField,T}
```

Gather values from the field for the system vector.

# Arguments

  * `self`: field;
  * `vec`: destination buffer;
  * `kind`: integer, kind of degrees of freedom to gather: default is `DOF_KIND_FREE`.
