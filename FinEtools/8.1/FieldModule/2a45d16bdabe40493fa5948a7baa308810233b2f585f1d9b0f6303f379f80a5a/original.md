```
setebc!(
    self::F,
    fenid::IT1,
    is_fixed::Bool,
    comp::IT2,
    val::T,
) where {F<:AbstractField,T<:Number,IT1<:Integer,IT2<:Integer}
```

Set the EBCs (essential boundary conditions).

`fenids`         - array of N node identifiers `is_fixed` = scaler Boolean: are the degrees of freedom being fixed (true)              or released (false), `comp` = integer, which  degree of freedom (component), `val` = array of N values of type T

Note:  Any call to `setebc!()` potentially changes the current assignment which degrees of freedom are free and which are fixed and therefore is presumed to invalidate the current degree-of-freedom numbering.
