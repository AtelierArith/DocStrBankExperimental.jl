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

ドライバーは、指定された関数 `f` を通じて、点 `x` での次数 `degree` までの単変数テイラー多項式を伝播させます。`keep` フラグは、テイラー多項式に対する後方モード計算のためにテープを準備するために使用されます。`tape_id` はテープの識別子を指定し、フラグ `reuse_tape` はテープの作成を抑制するために使用されるべきです。詳細はガイドに記載されています: [Univariate Taylor Polynomial Propagation](@ref).
