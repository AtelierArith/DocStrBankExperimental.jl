```
PeriodicDirichlet(u::Symbol, facet_mapping, components=nothing)
PeriodicDirichlet(u::Symbol, facet_mapping, R::AbstractMatrix, components=nothing)
PeriodicDirichlet(u::Symbol, facet_mapping, f::Function, components=nothing)
```

フィールド `u` に対して、`facet_mapping` で与えられたファセットペアに対する周期的ディリクレ境界条件を作成します。このマッピングは [`collect_periodic_facets`](@ref) を使って計算できます。この制約は、ミラーファセット上の自由度が、対応するイメージファセット上の自由度に制約されることを保証します。`components` は、この条件によって指定される `u` の成分を指定します。デフォルトでは、`u` のすべての成分が指定されます。

マッピングが座標軸に沿っていない場合（例えば、回転している場合）、回転行列 `R` をコンストラクタに渡す必要があります。この行列は、ミラーファセット上の自由度をイメージファセットに回転させます。これはベクトル値の問題にのみ適用されることに注意してください。

不均一な周期的制約を構築するために、関数 `f` を渡すことが可能です。これは現在、周期性が座標軸に沿っている場合にのみサポートされています。

詳細については、[周期境界条件](@ref) に関するマニュアルのセクションを参照してください。
