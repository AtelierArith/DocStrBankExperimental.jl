```
nonlinear_expr_string(
    model::GenericModel,
    mode::MIME,
    c::MOI.Nonlinear.Expression,
)
```

モデルに属する非線形式 `c` の文字列表現を、`mode` に基づいて返します。

!!! compat
    この関数は、従来の非線形インターフェースの一部です。[非線形モデリング](@ref) に記載されている新しい非線形インターフェースの使用を検討してください。

