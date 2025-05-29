```
colored_noise(rng = Random.default_rng(); n::Int = 500, ρ, σ = 0.1, transform = true)
```

`n` 個のカラーノイズのポイントを生成します。`ρ` は隣接サンプル間の望ましい相関です。ノイズは平均0、標準偏差 `σ` の正規分布から引き出されます。`transform = true` の場合、データを二次非線形静的歪みを使用して変換します。
