```
heartbeat = HeartBeat(circumferential_strain, radial_strain, longitudinal_strainl, time, spins)
```

# 引数

  * `circumferential_strain`: (`::Real`) 縮小パラメータ
  * `radial_strain`: (`::Real`) 縮小パラメータ
  * `longitudinal_strain`: (`::Real`) 縮小パラメータ
  * `time`: (`::TimeCurve{T<:Real}`) 動きに関する時間情報
  * `spins`: (`::AbstractSpinSpan`) 動きに影響を受けるスピンインデックス

# 戻り値

  * `heartbeat`: (`::Motion`) [`HeartBeat`](@ref) アクションを持つモーション構造体

# 例

```julia-repl
julia> heartbeat = HeartBeat(-0.3, -0.2, 0.0, TimeRange(0.0, 1.0), SpinRange(1:10))
```
