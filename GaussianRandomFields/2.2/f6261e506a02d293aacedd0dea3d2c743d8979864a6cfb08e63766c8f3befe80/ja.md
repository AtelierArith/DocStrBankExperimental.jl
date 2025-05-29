```
KarhunenLoeve(n)
```

`n`項を使用したカルフネン-ロエーヴ（KL）展開を用いた[`GaussianRandomFieldGenerator`](@ref)を返します。

# `GaussianRandomField`のオプション引数

  * `quad::QuadratureRule`: 積分方程式に使用される数値積分法（[`QuadratureRule`](@ref)を参照）、デフォルトは`EOLE()`です。
  * `nq::Integer`: 各次元の数値積分点の数で、`nq^d > n`が必要です。デフォルトは`nq = ceil(n^(1/d))`です。
  * `eigensolver::EigenSolver`: 固有値分解に使用するメソッド（[`AbstractEigenSolver`](@ref)を参照）。デフォルトは`EigenSolver()`です。

# 例

```jldoctest label1
julia> cov = CovarianceFunction(2, Matern(.3, 1))
2d Matérn共分散関数 (λ=0.3, ν=1.0, σ=1.0, p=2.0)

julia> pts = range(0, stop=1, length=51)
0.0:0.02:1.0

julia> grf = GaussianRandomField(cov, KarhunenLoeve(300), pts, pts)
2d Matérn共分散関数 (λ=0.3, ν=1.0, σ=1.0, p=2.0)を用いた51×51の構造化グリッド上のガウスランダムフィールドで、300項のKL展開を使用

julia> plot_eigenvalues(grf); # 固有値の減衰をプロット

julia> plot_eigenfunction(grf, 4); # 第4の固有関数をプロット

```

展開に使用される項`n`が多いほど、近似は良くなります。

```jldoctest label1; setup=:(import Random; Random.seed!(12345))
julia> for n in [1, 2, 5, 10, 20, 50, 100, 200, 500, 1000]
           grf = GaussianRandomField(cov, KarhunenLoeve(n), pts, pts)
           @printf "%.8f\n" rel_error(grf)
       end
0.69838285
0.45494187
0.23231278
0.10079295
0.02647020
0.00978427
0.00356549
0.00107191
0.00019810
0.00004085

```

!!! note
    技術的には、KL展開はナイストロム法を使用して計算されます。非構造化グリッドの場合、バウンディングボックスアプローチを使用します。これが望ましくない場合は、`Spectral`メソッドを使用してみてください。


!!! warning
    固有値の減衰における*エンド効果*を避けるために、`nq^d ≥ 5n`を選択してください。


```jldoctest label1
julia> grf = GaussianRandomField(cov, KarhunenLoeve(300), pts, pts, quad=GaussLegendre())
2d Matérn共分散関数 (λ=0.3, ν=1.0, σ=1.0, p=2.0)を用いた51×51の構造化グリッド上のガウスランダムフィールドで、300項のKL展開を使用

julia> grf = GaussianRandomField(cov, KarhunenLoeve(300), pts, pts, nq=40)
2d Matérn共分散関数 (λ=0.3, ν=1.0, σ=1.0, p=2.0)を用いた51×51の構造化グリッド上のガウスランダムフィールドで、300項のKL展開を使用

```

参照: [`Cholesky`](@ref), [`Spectral`](@ref), [`CirculantEmbedding`](@ref)
