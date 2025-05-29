```
CirculantEmbedding()
```

[`GaussianRandomFieldGenerator`](@ref) を返し、FFTを使用してガウスランダムフィールドのサンプルを計算します。

!!! warning
    循環埋め込みは、点が構造化グリッド上に指定されている場合にのみ適用できます。


# `GaussianRandomField` のオプション引数

  * `minnpadding::Integer`: 最小パディング量。
  * `measure::Bool`: [`sample`](@ref) メソッドの効率を高めるためにFFTを最適化します。デフォルトは `true` です。
  * `primes::Bool`: 共分散行列の最小循環埋め込みのサイズは、小さな素数（2、3、5、7）の積として書くことができます。デフォルトは `false` です。

# 例

```jldoctest
julia> cov = CovarianceFunction(2, Matern(.1, 1))
2d Matérn covariance function (λ=0.1, ν=1.0, σ=1.0, p=2.0)

julia> pts = range(0, stop=1, length=51)
0.0:0.02:1.0

julia> grf = GaussianRandomField(cov, CirculantEmbedding(), pts, pts)
Gaussian random field with 2d Matérn covariance function (λ=0.1, ν=1.0, σ=1.0, p=2.0) on a 51×51 structured grid, using a circulant embedding

julia> contourf(grf);

julia> plot_eigenvalues(grf);

```

!!! note
    適切な順序で、ガウスランダムフィールドの共分散行列は (ネストされたブロック) トプリッツ行列です。この行列は、FFTを使用して急速に計算できる固有値を持つ、より大きな (ネストされたブロック) 循環行列に埋め込むことができます。ここでの難しさは、共分散行列が正定値半定義であるにもかかわらず、その循環拡張は一般にはそうではないことです。対策として、オプションフラグ `minpadding` を使用して、関心のある領域の外にいわゆる *ゴーストポイント* を追加することができます。


```jldoctest; filter=r"^[┌│└].*$"s
julia> cov = CovarianceFunction(2, Matern(.3, 1))
2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0)

julia> pts = range(0, stop=1, length=51)
0.0:0.02:1.0

julia> grf = GaussianRandomField(cov, CirculantEmbedding(), pts, pts);
┌ Warning: 318 negative eigenvalues ≥ -0.5828339433508111 detected, Gaussian random field will be 
│         approximated (ignoring all negative eigenvalues); increase padding if possible
└ @ GaussianRandomFields ~/.julia/dev/GaussianRandomFields/src/generators/circulant_embedding.jl:94
Gaussian random field with 2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0) on a 51×51 structured grid, using a circulant embedding

julia> grf = GaussianRandomField(cov, CirculantEmbedding(), pts, pts, minpadding=79)
Gaussian random field with 2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0) on a 51×51 structured grid, using a circulant embedding

```

参照: [`Cholesky`](@ref), [`Spectral`](@ref), [`KarhunenLoeve`](@ref)
