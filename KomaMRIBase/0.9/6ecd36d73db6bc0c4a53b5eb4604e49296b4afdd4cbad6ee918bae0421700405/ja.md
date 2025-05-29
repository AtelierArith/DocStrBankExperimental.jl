```
rotate = Rotate(pitch, roll, yaw, spins)
```

# 引数

  * `pitch`: (`::Real`, `[º]`) x軸の回転
  * `roll`: (`::Real`, `[º]`) y軸の回転
  * `yaw`: (`::Real`, `[º]`) z軸の回転
  * `time`: (`::TimeCurve{T<:Real}`) 動きに関する時間情報
  * `spins`: (`::AbstractSpinSpan`) 動きに影響を受けるスピンインデックス

# 戻り値

  * `rotate`: (`::Motion`) [`Rotate`](@ref) アクションを持つモーション構造体

# 例

```julia-repl
julia> rotate = Rotate(15.0, 0.0, 20.0, TimeRange(0.0, 1.0), SpinRange(1:10))
```
