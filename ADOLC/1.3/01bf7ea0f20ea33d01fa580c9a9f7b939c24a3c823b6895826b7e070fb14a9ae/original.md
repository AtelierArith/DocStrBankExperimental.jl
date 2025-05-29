```
univariate_tpp(
    f,
    x::Union{Cdouble,Vector{Cdouble}},
    degree::Integer;
    keep::Bool=false,
    tape_id::Integer=0,
    reuse_tape::Bool=false,
)
```

The driver propagates univariate Taylor polynomials through the given function `f` at the point  `x` up to `degree`. The `keep` flag is used to prepare the tape for subsequent reverse-mode computations on the Taylor polynomial. The `tape_id` specifies the identifier of the tape and the flag `reuse_tape` should  be used for suppressing the tape creation. More information is given in the guide: [Univariate Taylor Polynomial Propagation](@ref).
