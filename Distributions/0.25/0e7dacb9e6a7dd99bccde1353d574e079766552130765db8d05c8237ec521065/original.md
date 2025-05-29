A Julia package for probability distributions and associated functions.

API overview (major features):

  * `d = Dist(parameters...)` creates a distribution instance `d` for some distribution `Dist` (see choices below) with the specified `parameters`
  * `rand(d, sz)` samples from the distribution
  * `pdf(d, x)` and `logpdf(d, x)` compute the probability density or log-probability density of `d` at `x`
  * `cdf(d, x)` and `ccdf(d, x)` compute the (complementary) cumulative distribution function at `x`
  * `quantile(d, p)` is the inverse `cdf` (see also `cquantile`)
  * `mean(d)`, `var(d)`, `std(d)`, `skewness(d)`, `kurtosis(d)` compute moments of `d`
  * `fit(Dist, xs)` generates a distribution of type `Dist` that best fits the samples in `xs`

These represent just a few of the operations supported by this package; users are encouraged to refer to the full documentation at https://JuliaStats.github.io/Distributions.jl/stable/ for further information.

Supported distributions:

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
