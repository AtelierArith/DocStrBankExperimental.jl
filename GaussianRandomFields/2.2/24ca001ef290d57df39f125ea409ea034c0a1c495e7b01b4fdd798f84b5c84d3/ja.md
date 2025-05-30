```
Spectral()
```

共分散行列のスペクトル（固有値）分解に基づく[`GaussianRandomFieldGenerator`](@ref)を返します。

# `GaussianRandomField`のオプション引数

  * `n::Integer`: 計算する固有値の数。デフォルトでは、すべての固有値を計算します。
  * `eigensolver::EigenSolver`: 固有値分解に使用する方法（[`AbstractEigenSolver`](@ref）を参照）。デフォルトは`EigenSolver()`です。

# 例

```jldoctest
julia> cov = CovarianceFunction(2, Matern(.3, 1))
2d Matérン共分散関数 (λ=0.3, ν=1.0, σ=1.0, p=2.0)

julia> pts = range(0, stop=1, length=51)
0.0:0.02:1.0

julia> grf = GaussianRandomField(cov, Spectral(), pts, pts)
2d Matérn共分散関数 (λ=0.3, ν=1.0, σ=1.0, p=2.0)を用いた51×51の構造化グリッド上のガウス乱数場、スペクトル分解を使用

julia> heatmap(grf);

```

!!! tip
    共分散行列の評価が高コストすぎる場合は、カーニューネ・ロエーブ展開を使用してみてください。


これは、切り取られたKL展開を使用して有限要素メッシュ上でガウス乱数場を計算する際にも便利です。以下は、L字型領域で最初の10個の固有関数を計算する例です。

```jldoctest
julia> cov = CovarianceFunction(2, Matern(.3, 1))
2d Matérn共分散関数 (λ=0.3, ν=1.0, σ=1.0, p=2.0)

julia> p, t = Lshape();

julia> grf = GaussianRandomField(cov, Spectral(), p, t, n=10)
2d Matérn共分散関数 (λ=0.3, ν=1.0, σ=1.0, p=2.0)を用いた998点と1861要素のメッシュ上のガウス乱数場、スペクトル分解を使用

```

参照: [`Cholesky`](@ref), [`KarhunenLoeve`](@ref), [`CirculantEmbedding`](@ref)
