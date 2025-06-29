`rainfall_poisson(n, α, λ)`

ポアソン過程を使用して降雨を生成します。

# 引数

  * `n::Integer`: イベントの数。
  * `α::Float64`: 平均降雨深度。
  * `λ::Float64`: 降雨イベントの間隔 (1/d)。

降雨を日単位よりも小さい時間スケールでシミュレートする必要がある場合は、`λ` に dt を掛けてください。

# 例

```
n = 30
α = 0.75
λ = 0.45
rain = rainfall_poisson(n, α, λ)
```
