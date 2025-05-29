```
mt_ccvf(S1, S2; <keyword arguments>)
```

二変量マルチテーパー交差共分散/交差相関関数を2つの時系列から計算します

...

# 引数

  * `S1::Vector{T} where T<:Number`: 最初の時系列を含むベクトル
  * `S2::Vector{T} where T<:Number`: 2番目の時系列を含むベクトル
  * `typ::Symbol`: 交差共分散関数を計算するか(:ccvf)、または交差相関関数を計算するか(:ccf)
  * `NW::Float64 = 4.0`: 推定の時間帯域幅の積
  * `K::Int64 = 6`: スレピアンテーパーの数、2*NW以下でなければならない
  * `dt::Float64`: 時間単位でのサンプリングレート
  * `ctr::Bool`: マルチテーパースペクトルを計算する前に平均を除去するかどうか
  * `pad::Float64 = 1.0`: シリーズをパディングするための係数、すなわちスペクトルの長さは時系列の長さのpad倍になります。
  * `dpVec::Union{Matrix{Float64},Nothing} = nothing`: 事前に計算されたdpssの行列

...

...

# 出力

  * `MtCrossCovarianceFunction` 構造体、上記の`typ`入力の選択に依存します。

...

参照: [`multispec`](@ref)
