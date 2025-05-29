```
bspec(time, dat, W, K, bet, nz; <keyword arguments>)
```

p個の不均等に間隔を置かれた時系列のブロネススペクトルとコヒーレンスを計算します

...

# 位置引数

  * `time::Vector{T} where T<:Number`: 時間を含むベクター
  * `dat::Matrix{Vector{P}} where T<:Number`: 列に時系列を含む行列
  * `W::Float64`: 推定の帯域幅
  * `K::Int64`: スレピアンテーパーの数、2*NW以下でなければならない
  * `bet::Float64`: ナイキスト周波数
  * `nz::Union{Float64,Int64} = length(t)`: 周波数の数

# キーワード引数

  * `outp::Symb = :coh`: 出力、交差スペクトルの場合は `:cross`、または `:coh`（デフォルト）
  * `Ftest::Bool = false`: F検定を計算するかどうか

...

...

# 出力

  * ブロネススペクトルとコヒーレンスを含む tuple(Vector{MTSpectrum},Matrix{MTCoherence},Nothing)

...

...

# 使用例

```<julia>
N = 256
t = collect(1:N).^(1.05)
W = 0.008
K = 5
x = randn(N)
y = randn(N) # 非コヒーレント
M = 2*N
beta = 0.5
S = bspec(t, hcat(x, y), W, K, beta, M, outp = :coh, Ftest = true)
```

...

参照: [`multispec`](@ref), [`mdmultispec`](@ref), [`mdslepian`](@ref), [`gpss`](@ref) ```
