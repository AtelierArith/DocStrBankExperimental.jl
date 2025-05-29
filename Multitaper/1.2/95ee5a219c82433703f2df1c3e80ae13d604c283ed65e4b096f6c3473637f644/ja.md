```
mdmultispec(tt, x; <キーワード引数>)
```

同じ欠損データ（ギャップ）を持つ複数の時系列のためのマルチテーパーコヒーレンス推定

...

# 引数

## キーワード引数

  * `tt::Vector{T} where T<:Real`: 時間インデックスを含むベクトル
  * `x::Matrix{P} where P<:Number`: 行列の列にある時系列

## 位置引数

  * `bw = 5/length(tt)`: 推定の帯域幅
  * `k::Int64 = 2*bw*length(x)-1`: スレピアンテーパーの数、`<= 2*bw*length(x)` でなければならない
  * `dt = tt[2]-tt[1]`: 時間単位でのサンプリングレート
  * `nz = 0.0`: ゼロパディング係数
  * `Ftest::Bool = false`: F検定のp値を計算
  * `jk::Bool = true`: ジャックナイフ信頼区間を計算
  * `lambdau::Union{Tuple{Array{Float64,1},Array{Float64,2}},Nothing} = nothing`:

事前に計算されたスレピアン

...

...

# 出力

  * `Tuple{Vector{MTSpectrum},Matrix{MTCoherence},Nothing}` 構造体はスペクトル、

コヒーレンス、およびT^2検定の有意性を含む（現在は何も返さないように設定されている）

...

参照: [`multispec`](@ref), [`mdslepian`](@ref) ```
