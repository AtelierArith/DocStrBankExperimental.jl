```
univariate_tpp!(
    res::CxxMatrix,
    f,
    x::Union{Cdouble,Vector{Cdouble}},
    degree::Integer,
    init_tp::CxxMatrix;
    keep::Bool=false,
    tape_id::Integer=0,
    reuse_tape::Bool=false,
)
```

A version of the [`univariate_tpp`](@ref) driver that allows a user to pass in a pre-allocated [CxxMatrix](@ref "Working with C++ Memory"). More information is given in the guide: [Univariate Taylor Polynomial Propagation](@ref).
