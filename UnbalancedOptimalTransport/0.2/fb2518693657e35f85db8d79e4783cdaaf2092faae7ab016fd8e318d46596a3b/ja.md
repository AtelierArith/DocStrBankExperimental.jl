```
function OT!(
    D::AbstractDivergence,
    C,
    a::DiscreteMeasure,
    b::DiscreteMeasure,
    ϵ = 1e-1;
    C = (x, y) -> norm(x - y),
    kwargs...,
) -> Number
```

`a`と`b`の間の最適輸送コストを計算します。[`unbalanced_sinkhorn!`](@ref)を使用します。パラメータとキーワード引数の意味についてはその関数を参照してください。[[SFVTP19](@ref)]の式(15)を実装しています。
