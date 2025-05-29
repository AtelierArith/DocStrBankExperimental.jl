```
multispec(S1; <キーワード引数>)
```

ユニバリアントマルチテーパースペクトルを計算し、いくつかの追加機能を提供します。

...

# 引数

  * `S1::Vector{T} where T<:Float64`: 時系列を含むベクトル
  * `NW::Float64 = 4.0`: 推定の時間帯域幅積
  * `K::Int64 = 6`: スレピアンテーパーの数、2*NW以下でなければならない
  * `dt::Float64`: 時間単位でのサンプリングレート
  * `ctr::Bool`: マルチテーパースペクトルを計算する前に平均を除去するかどうか
  * `pad::Float64 = 1.0`: シリーズをパディングするための係数、すなわちスペクトルの長さはパッドと時系列の長さの積になります。
  * `dpVec::Union{Matrix{Float64},Nothing} = nothing`: 事前に計算されたdpssの行列
  * `egval::Union{Vector{Float64},Nothing} = nothing`: 前述のdpssの集中度のベクトル
  * `guts::Bool = false`: 出力構造体に固有係数を返すかどうか
  * `a_weight::Bool = true`: 適応重み付けを使用するかどうか
  * `Ftest::Bool = true`: F検定のp値を計算する
  * `highres::Bool = false`: "高解像度"のスペクトル推定を返すかどうか
  * `jk::Bool = true`: ジャックナイフ信頼区間を計算する
  * `Tsq::Union{Vector{Int64},Vector{Vector{Int64}},Nothing} = nothing`: 複数の線成分に対してT二乗検定を計算する周波数インデックス。デフォルトはなし。

...

...

# 出力

  * スペクトルを含む`MTSpectrum`構造体

...

参照: [`dpss_tapers`](@ref), [`MTSpectrum`](@ref), [`mdmultispec`](@ref), [`mdslepian`](@ref)
