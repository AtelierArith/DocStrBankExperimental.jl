```
mt_cepstrum(S1; <keyword arguments>)
```

入力時系列からマルチテーパーケプストラムを計算します。 ...

# 引数

  * `S1::Vector{T} where T<:Number`: 時系列を含むベクトル
  * `NW::Float64 = 4.0`: 推定の時間帯域幅積
  * `K::Int64 = 6`: スレピアンテーパーの数、2*NW以下でなければならない
  * `dt::Float64`: 時間単位でのサンプリングレート
  * `ctr::Bool`: マルチテーパースペクトルを計算する前に平均を除去するかどうか
  * `pad::Float64 = 1.0`: シリーズをパディングするための係数、すなわちスペクトルの長さはパッドと時系列の長さの積になります。
  * `dpVec::Union{Matrix{Float64},Nothing} = nothing`: 事前に計算されたdpssの行列
  * `egval::Union{Vector{Float64},Nothing} = nothing`: 前述のdpssの集中度のベクトル
  * `a_weight::Bool = true`: 適応重み付けを使用するかどうか

...

...

# 出力

  * ケプストラムを含む`MTCepstrum`構造体

...

参照: [`multispec`](@ref)
