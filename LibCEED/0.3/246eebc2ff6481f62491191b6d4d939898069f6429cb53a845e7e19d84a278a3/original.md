```
apply(r::ElemRestriction, u::AbstractVector; tmode=NOTRANSPOSE)
```

Use the [`ElemRestriction`](@ref) to convert from L-vector to an E-vector (or apply the tranpose operation). The input is given by `u`, and the result is returned as an array of type `Vector{CeedScalar}`.
