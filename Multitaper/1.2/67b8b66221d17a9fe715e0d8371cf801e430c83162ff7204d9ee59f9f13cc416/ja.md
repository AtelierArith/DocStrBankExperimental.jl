```
bspec(time, dat1, dat2, W, K, bet, nz; <keyword arguments>)
```

2つの不均等に間隔を置かれた時系列のブロネズコヒーレンスまたはクロススペクトルを計算します

...

# 位置引数

  * `time::Vector{T} where T<:Number`: 時間を含むベクトル
  * `dat1::Union{Vector{P}, EigenCoefficient} where P<:Number`: 最初の時系列を含むベクトル
  * `dat2::Union{Vector{P}, EigenCoefficient} where P<:Number`: 2番目の時系列を含むベクトル
  * `W::Float64`: 推定の帯域幅
  * `K::Int64`: スレピアンテーパーの数、<= 2*NWでなければならない
  * `bet::Float64`: ナイキスト周波数
  * `nz::Union{Float64,Int64} = length(t)`: 周波数の数

# キーワード引数

  * `outp::Symb = :coh`: 出力、クロススペクトルの場合は `:cross`、または `:coh`（デフォルト）
  * `params::Union{MTParameters,Nothing} = nothing`: パラメータ構造体、x,yがEigenCoefficientのときに重要
  * `Ftest::Bool = false`: F検定を計算するかどうか

...

...

# 出力

  * ブロネズコヒーレンスを含むMTCoherence

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
S = bspec(t, x, y, W, K, M, beta)
```

...

参照: [`multispec`](@ref), [`mdmultispec`](@ref), [`mdslepian`](@ref), [`gpss`](@ref) ```
