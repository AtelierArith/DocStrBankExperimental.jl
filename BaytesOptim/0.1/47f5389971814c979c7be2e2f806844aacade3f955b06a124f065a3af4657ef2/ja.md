```julia
struct ConfigSGD{R<:Real, A<:BaytesCore.UpdateBool} <: BaytesCore.AbstractConfiguration
```

SGDオプティマイザのデフォルト設定。

# フィールド

  * `magnitude_penalty::Real`: ログ事後に `-0.5 * magnitude_penalty * sum(abs2, q)` を追加します **ローカルオプティマムを見つけるとき**。これにより、通常ではない高密度のエッジ領域に入るのを避けるのに役立ちます（例：マルチレベルモデル）。
  * `magnitude_adaption::BaytesCore.UpdateBool`: 各ステップのために大きさを反復的に適応させます ~ 現在は実装されていません
  * `iterations::Int64`: 最適化アルゴリズムにおける最大反復回数。モードを見つける必要はなく、ローカルモードでさえ必要ありません。ただし、合理的な領域にいる必要があります。
  * `difforder::BaytesDiff.DiffOrderOne`: 伝播ステップを実行するために必要な目的関数の微分可能な順序
