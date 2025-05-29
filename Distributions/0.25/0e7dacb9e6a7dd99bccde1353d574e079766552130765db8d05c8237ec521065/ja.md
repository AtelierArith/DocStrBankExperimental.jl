確率分布と関連する関数のためのJuliaパッケージ。

APIの概要（主な機能）：

  * `d = Dist(parameters...)` は、指定された `parameters` を持つ分布 `Dist` のインスタンス `d` を作成します（以下の選択肢を参照）
  * `rand(d, sz)` は、分布からサンプリングします
  * `pdf(d, x)` と `logpdf(d, x)` は、`x` における `d` の確率密度または対数確率密度を計算します
  * `cdf(d, x)` と `ccdf(d, x)` は、`x` における（補完的）累積分布関数を計算します
  * `quantile(d, p)` は逆 `cdf` です（`cquantile` も参照）
  * `mean(d)`, `var(d)`, `std(d)`, `skewness(d)`, `kurtosis(d)` は、`d` のモーメントを計算します
  * `fit(Dist, xs)` は、`xs` のサンプルに最も適合する `Dist` 型の分布を生成します

これらはこのパッケージがサポートする操作のほんの一部です。ユーザーは、さらなる情報のために https://JuliaStats.github.io/Distributions.jl/stable/ の完全なドキュメントを参照することをお勧めします。

サポートされている分布：

```
Arcsine, Bernoulli, Beta, BetaBinomial, BetaPrime, Binomial, Biweight,
Categorical, Cauchy, Censored, Chi, Chisq, Cosine, DiagNormal, DiagNormalCanon,
Dirichlet, DiscreteUniform, DoubleExponential, EdgeworthMean,
EdgeworthSum, EdgeworthZ, Erlang,
Epanechnikov, Exponential, FDist, FisherNoncentralHypergeometric,
Frechet, FullNormal, FullNormalCanon, Gamma, GeneralizedPareto,
GeneralizedExtremeValue, Geometric, Gumbel, Hypergeometric,
InverseWishart, InverseGamma, InverseGaussian, IsoNormal,
IsoNormalCanon, JohnsonSU, Kolmogorov, KSDist, KSOneSided, Kumaraswamy,
Laplace, Levy, Lindley, LKJ, LKJCholesky,
Logistic, LogNormal, MatrixBeta, MatrixFDist, MatrixNormal,
MatrixTDist, MixtureModel, Multinomial,
MultivariateNormal, MvLogNormal, MvNormal, MvNormalCanon,
MvNormalKnownCov, MvTDist, NegativeBinomial, NoncentralBeta, NoncentralChisq,
NoncentralF, NoncentralHypergeometric, NoncentralT, Normal, NormalCanon,
NormalInverseGaussian, Pareto, PGeneralizedGaussian, Poisson, PoissonBinomial,
QQPair, Rayleigh, Rician, Skellam, Soliton, StudentizedRange, SymTriangularDist, TDist, TriangularDist,
Triweight, Truncated, Uniform, UnivariateGMM,
VonMises, VonMisesFisher, WalleniusNoncentralHypergeometric, Weibull,
Wishart, ZeroMeanIsoNormal, ZeroMeanIsoNormalCanon,
ZeroMeanDiagNormal, ZeroMeanDiagNormalCanon, ZeroMeanFullNormal,
ZeroMeanFullNormalCanon
```
