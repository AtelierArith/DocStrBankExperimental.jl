```
welch(S1, nsegments; <keyword arguments>)
```

入力時系列から始まる単変量マルチテーパーWelchスペクトルを計算します。

...

# 引数

  * `S1:Vector{T} where T<:Number`: 時系列を含むベクター
  * `nsegments::Int64`: 時系列を分割するセグメントの数
  * `overlap::Float64 = 0.5`: セグメント間の重複量を考慮する0から1の間の数
  * `NW::Float64 = 4.0`: 推定の時間帯域積
  * `K::Int64 = 6`: スレピアンテーパーの数、2*NW以下でなければならない
  * `dt::Float64`: 時間単位でのサンプリングレート
  * `ctr::Bool`: マルチテーパーのスペクトルを計算する前に平均を除去するかどうか
  * `pad::Float64 = 1.0`: シリーズをパディングするための係数、すなわちスペクトルの長さは

時系列の長さのパディング倍になります。

  * `dpVec::Union{Matrix{Float64},Nothing} = nothing`: 事前に計算された場合のdpssの行列
  * `egval::Union{Vector{Float64},Nothing} = nothing`: 前述のdpssの濃度のベクター
  * `guts::Bool = false`: 出力構造体に固有係数を返すかどうか
  * `a_weight::Bool = true`: 適応重み付けを使用するかどうか

...

...

# 出力

  * `MTSpectrum`構造体、上記の`outp`の選択に依存
  * 効果的帯域幅を含む`Float64`

...

参照: [`multispec`](@ref)
