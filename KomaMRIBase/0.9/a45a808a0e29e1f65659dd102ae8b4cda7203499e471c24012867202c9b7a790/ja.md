```
translate = Translate(dx, dy, dz, time, spins)
```

# 引数

  * `dx`: (`::Real`, `[m]`) x方向の移動量
  * `dy`: (`::Real`, `[m]`) y方向の移動量
  * `dz`: (`::Real`, `[m]`) z方向の移動量
  * `time`: (`::TimeCurve{T<:Real}`) 動きに関する時間情報
  * `spins`: (`::AbstractSpinSpan`) 動きに影響を受けるスピンインデックス

# 戻り値

  * `translate`: (`::Motion`) Motion構造体

# 例

```julia-repl
julia> translate = Translate(0.01, 0.02, 0.03, TimeRange(0.0, 1.0), SpinRange(1:10))
```
