```
assemble!(self::SysvecAssembler{T}, vec::MV,
  dofnums::D) where {T<:Number, MV<:AbstractArray{T}, D<:AbstractArray{FInt}}
```

Assemble an elementwise vector.

The method assembles a column element vector using the vector of degree of freedom numbers for the rows.
