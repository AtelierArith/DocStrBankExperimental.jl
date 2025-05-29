```
flowpath = FlowPath(dx, dy, dz, spin_reset, time, spins)
```

# 引数

  * `dx`: (`::AbstractArray{T<:Real}`, `[m]`) x方向の変位
  * `dy`: (`::AbstractArray{T<:Real}`, `[m]`) y方向の変位
  * `dz`: (`::AbstractArray{T<:Real}`, `[m]`) z方向の変位
  * `spin_reset`: (`::AbstractArray{Bool}`) スピン状態リセットフラグ
  * `time`: (`::TimeCurve{T<:Real}`) 動きに関する時間情報
  * `spins`: (`::AbstractSpinSpan`) 動きに影響を受けるスピンインデックス

# 戻り値

  * `flowpath`: (`::Motion`) [`FlowPath`](@ref) アクションを持つモーション構造体

# 例

```julia-repl
julia> flowpath = FlowPath(
          [0.01 0.02; 0.02 0.03], 
          [0.02 0.03; 0.03 0.04], 
          [0.03 0.04; 0.04 0.05], 
          [false false; false true],
          TimeRange(0.0, 1.0), 
          SpinRange(1:10)
       )
```
