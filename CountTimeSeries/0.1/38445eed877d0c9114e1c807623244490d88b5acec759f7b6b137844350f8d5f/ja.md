```
parameter(β0, α, β, η, ϕ, ω)
```

カウントデータモデルのパラメータの構造。

  * `β0`: 切片パラメータ
  * `α`: 自己回帰のためのパラメータ
  * `β`: MA部分/過去の平均のためのパラメータ
  * `η`: 回帰変数のパラメータ
  * `ϕ`: 過剰分散パラメータ（負の二項分布またはGPoisson）
  * `ω`: ゼロインフレーション確率

詳細については、[Documentation](https://github.com/ManuelStapper/CountTimeSeries.jl/blob/master/CountTimeSeries_documentation.pdf)を参照してください。
