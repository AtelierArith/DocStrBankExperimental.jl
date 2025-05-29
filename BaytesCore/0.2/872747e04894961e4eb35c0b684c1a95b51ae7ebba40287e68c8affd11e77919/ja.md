```julia
struct PrintDefault
```

サンプリング後の要約統計を印刷するためのデフォルト引数。

# フィールド

  * `Ndigits::Int64`: 要約統計を丸めるための桁数。
  * `quantiles::Vector{Float64}`: 要約統計のための分位数。
