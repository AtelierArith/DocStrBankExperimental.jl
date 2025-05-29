```
mdmultispec(tt, x, y; <keyword arguments>)
```

欠損データ（ギャップ）のある時系列のためのマルチテーパーコヒーレンス推定

...

# 引数

## 位置引数

  * `tt::Vector{T} where T<:Real`: 時間インデックスを含むベクトル
  * `x::Vector{P} where P<:Number`: データベクトル 1
  * `y::Vector{Q} where Q<:Number`: データベクトル 2

## キーワード引数

  * `bw = 5/length(tt)`: 推定の帯域幅
  * `k::Int64 = 2*bw*length(x)-1`: スレピアンテーパーの数、`<= 2*bw*length(x)`でなければならない
  * `dt = tt[2]-tt[1]`: 時間単位でのサンプリングレート
  * `nz = 0.0`: ゼロパディング係数
  * `Ftest::Bool = true`: F検定のp値を計算
  * `jk::Bool = true`: ジャックナイフ信頼区間を計算
  * `lambdau::Union{Tuple{Array{Float64,1},Array{Float64,2}},Nothing} = nothing`: スレピアン、事前計算されている場合

...

...

# 出力

  * `pkg::MTCoherence` 構造体、コヒーレンスを含む

...

参照: [`multispec`](@ref), [`mdslepian`](@ref)
