```
setebc!(
    self::F,
    fenids::AbstractVector{IT},
    is_fixed::Bool,
    comp::AbstractVector{IT},
    val::T = 0.0,
) where {T<:Number, IT<:Integer}
```

Set the EBCs (essential boundary conditions).

`fenids` = array of N node identifiers `comp` = integer vector, which degree of freedom (component), `val` = scalar of type `T`, default is `0.0`

Note:  Any call to `setebc!()` potentially changes the current assignment which degrees of freedom are free and which are fixed and therefore is presumed to invalidate the current degree-of-freedom numbering.
