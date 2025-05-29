```
bspec(times, dat, W, K, beta, nz, Ftest)
```

不均等に間隔を置かれた時系列のブロネズスペクトルを計算します

...

# 位置引数

  * `times::Vector{T} where T<: Number`: 時間を含むベクター
  * `dat::Vector{T} where T<:Number`: 時系列を含むベクター
  * `W::Float64`: 推定の帯域幅
  * `K::Int64`: スレピアンテーパーの数、2*NW以下でなければならない
  * `beta::Float64`: 推定されたプロセスの帯域幅（別名ナイキストレート）
  * `nz::Union{Float64,Int64} = length(t)`: 周波数の数
  * `Ftest::Bool = false`: F検定を計算するかどうか

...

...

# 出力

  * ブロネズスペクトルを含むMTSpectrum構造体

...

...

# 使用例

```<julia>
N = 256
t = collect(1:N).^(1.05)
W = 0.008
K = 5
x = randn(N)
bet = 0.5 / (last(t) / (N-1))
M = 2*N
S = bspec(t, x, W, K, bet, nz, true)
```

...

参照: [`multispec`](@ref), [`mdmultispec`](@ref), [`mdslepian`](@ref), [`gpss`](@ref)
