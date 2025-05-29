```
multispec(S1, S2; <キーワード引数>)
```

同じサンプリングを持つ2つの時系列が与えられたときに、マルチテーパー交差スペクトルまたはコヒーレンスを計算します。

...

# 引数

  * `S1::Union{Vector{T},EigenCoefficient} where T<:Number`: 最初の時系列を含むベクトル
  * `S2::Union{Vector{P},EigenCoefficient} where P<:Number`: 2番目の時系列を含むベクトル
  * `outp::Symbol`: 出力はコヒーレンスの場合は :coh、交差スペクトルの場合は :spec、または伝達関数の場合は :transf であることができます。
  * `NW::Float64 = 4.0`: 推定の時間帯域幅積
  * `K::Int64 = 6`: スレピアンテーパーの数、2*NW以下でなければなりません
  * `offset::Union{Float64,Int64} = 0`: オフセットコヒーレンスまたは交差スペクトルが必要な場合は非ゼロ値に設定します。Float64が使用される場合、これは最も近いFFTビンに変換されます。
  * `dt::Float64`: 時間単位でのサンプリングレート
  * `ctr::Bool`: マルチテーパーのスペクトルを計算する前に平均を除去するかどうか
  * `pad::Float64 = 1.0`: シリーズをパディングするための係数、すなわちスペクトルの長さは時系列の長さのパディング倍になります。
  * `dpVec::Union{Matrix{Float64},Nothing} = nothing`: 事前に計算された場合のdpssの行列
  * `guts::Bool = false`: 出力構造体に固有係数を返すかどうか
  * `jk::Bool = true`: ジャックナイフされた信頼区間を計算します
  * `Tsq::Union{Vector{Int64},Vector{Vector{Int64}},Nothing} = nothing`: 複数の線成分に対してT二乗検定を計算する周波数インデックス。デフォルトはなし。
  * `alph::Float64 = 0.05`: T二乗検定の有意性カットオフ

...

...

# 出力

  * `MTSpectrum`、`MTCoherence`、または `MTTransferFunction` 構造体は、`outp` 入力の選択に応じてスペクトル、コヒーレンス、または伝達関数を含みます。

...

参照: [`dpss_tapers`](@ref)、[`MTSpectrum`](@ref)、[`mdmultispec`](@ref)、[`mdslepian`](@ref)
