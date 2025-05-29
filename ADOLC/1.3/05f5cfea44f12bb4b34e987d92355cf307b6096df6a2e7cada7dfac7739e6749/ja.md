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

[`univariate_tpp`](@ref) ドライバーのバージョンで、初期テイラー多項式に対する追加の制御を可能にします。詳細はガイドに記載されています: [Univariate Taylor Polynomial Propagation](@ref).
