```
sinkhorn_divergence!(
    D::AbstractDivergence,
    C,
    a::DiscreteMeasure,
    b::DiscreteMeasure,
    ϵ = 1e-1;
    kwargs...,
) -> Number
```

`a` と `b` の間の不均衡シンクホルン発散を [[SFVTP19](@ref)] の定義 6 に従って計算します。[`unbalanced_sinkhorn!`](@ref) を使用します。パラメータとキーワード引数の意味についてはその関数を参照してください。`a` と `b` の最適な `dual_potential` を設定します。
