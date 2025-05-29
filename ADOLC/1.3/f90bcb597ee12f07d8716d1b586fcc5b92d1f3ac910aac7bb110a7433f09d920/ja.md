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

[`univariate_tpp`](@ref) ドライバーのバージョンで、ユーザーが事前に割り当てられた [CxxMatrix](@ref "Working with C++ Memory") を渡すことを可能にします。詳細はガイドに記載されています: [Univariate Taylor Polynomial Propagation](@ref).
