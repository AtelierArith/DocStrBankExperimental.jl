```
apply!(
    r::ElemRestriction,
    u::CeedVector,
    ru::CeedVector;
    tmode=NOTRANSPOSE,
    request=RequestImmediate(),
)
```

Use the [`ElemRestriction`](@ref) to convert from L-vector to an E-vector (or apply the tranpose operation). The input [`CeedVector`](@ref) is `u` and the result stored in `ru`.

If `tmode` is `TRANSPOSE`, then the result is added to `ru`. If `tmode` is `NOTRANSPOSE`, then `ru` is overwritten with the result.
