```julia
get_lims(x) -> Tuple{Any, Any}
get_lims(x, n) -> Tuple{Any, Any}

```

フィールド `x` の平均と標準偏差 ($\mu \pm n \sigma$) に基づいて、近似的な下限と上限を取得します。`x` が定数の場合、`1e-4` のマージンが強制されます。これは、特定の範囲を必要とする等高線プロット関数に必要です。
