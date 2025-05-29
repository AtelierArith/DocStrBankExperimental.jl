```
mdmultispec(tt, x; <キーワード引数>)
```

欠損データ（ギャップ）のある時系列のためのマルチテーパー電力スペクトル推定

...

# 引数

## 位置引数

  * `tt::Vector{T} where T<:Real`: 時間インデックスを含むベクトル
  * `x::Vector{P} where P<:Number`: データベクトル

## キーワード引数

  * `bw = 5/length(tt)`: 推定の帯域幅
  * `k::Int64 = 2*bw*length(x)-1`: スレピアンテーパーの数、`<= 2*bw*length(x)` でなければならない
  * `dt::T = tt[2]-tt[1]`: 時間単位でのサンプリングレート
  * `nz = 0.0`: ゼロパディング係数
  * `Ftest::Bool = true`: F検定のp値を計算する
  * `jk::Bool = true`: ジャックナイフ信頼区間を計算する
  * `dof::Bool = false`: 適応的に重み付けされたスペクトル推定の自由度を計算する
  * `lambdau::Union{Tuple{Array{Float64,1},Array{Float64,2}},Nothing} = nothing`:

スレピアン、事前計算されている場合 ...

...

# 出力

  * `pkg::MTSpectrum` 構造体、スペクトルを含む
  * `nu1::Vector{Float64}` 自由度を含むオプションのベクトル、`dof` キーワード引数が `true` に設定されている場合に与えられる。

...

参照: [`multispec`](@ref), [`mdslepian`](@ref)
