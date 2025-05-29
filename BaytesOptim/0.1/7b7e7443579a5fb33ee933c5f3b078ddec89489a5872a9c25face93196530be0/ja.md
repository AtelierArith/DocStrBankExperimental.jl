```julia
struct ConfigLBFG{R<:Real} <: BaytesCore.AbstractConfiguration
```

LBFGオプティマイザのデフォルト設定。

# フィールド

  * `magnitude_penalty::Real`: ログ事後に `-0.5 * magnitude_penalty * sum(abs2, q)` を追加します **ローカル最適解を見つけるとき**。これにより、通常ではない高密度のエッジ領域に入るのを避けるのに役立ちます（例：マルチレベルモデル）。
  * `iterations::Int64`: 最適化アルゴリズムの最大反復回数。モードを見つける必要はなく、ローカルモードさえも必要なく、合理的な領域にいるだけで構いません。
  * `difforder::BaytesDiff.DiffOrderOne`: 伝播ステップを実行するために必要な目的関数の微分順序
