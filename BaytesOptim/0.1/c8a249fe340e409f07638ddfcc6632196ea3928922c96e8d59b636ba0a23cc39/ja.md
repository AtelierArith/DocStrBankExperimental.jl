```julia
struct LBFGTune{R<:Real} <: BaytesCore.AbstractTune
```

最適化アルゴリズム全体で使用される情報を格納します。

# フィールド

  * `magnitude_penalty::Real`: ログ事後に `-0.5 * magnitude_penalty * sum(abs2, q)` を追加します **局所最適解を見つけるとき**。これにより、通常ではない高密度のエッジ領域に入るのを避けるのに役立ちます（例：多層モデル）。
  * `iterations::Int64`: 最適化アルゴリズムにおける最大反復回数。モードを見つける必要はなく、局所モードさえも必要なく、合理的な領域にいるだけで構いません。
