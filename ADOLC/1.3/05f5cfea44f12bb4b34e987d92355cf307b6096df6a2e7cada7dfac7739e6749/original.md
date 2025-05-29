```
univariate_tpp(
    f,
    x::Union{Cdouble,Vector{Cdouble}},
    degree::Integer,
    init_tp::CxxMatrix;
    keep::Bool=false,
    tape_id::Integer=0,
    reuse_tape::Bool=false,
)
```

Version of the [`univariate_tpp`](@ref) driver, which allows additional control over the initial Taylor polynomial.  More information is given in the guide: [Univariate Taylor Polynomial Propagation](@ref).
