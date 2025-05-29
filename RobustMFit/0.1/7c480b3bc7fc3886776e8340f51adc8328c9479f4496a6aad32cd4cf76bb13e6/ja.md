```
AVar(d::UnivariateDistribution, spec::MSetting, biasCorr::Union{Symbol, String})
AVar(d::UnivariateDistribution, spec::Vector{MSetting}, biasCorr::Union{Symbol, String})
AVar(x::Vector{Real}, d::UnivariateDistribution, spec::MSetting, biasCorr::Union{Symbol, String})
AVar(x::Vector{Real}, d::UnivariateDistribution, spec::Vector{MSetting}, biasCorr::Union{Symbol, String})
```

M推定量の漸近分散/共分散行列。

適合した分布 `d` に複数のパラメータがある場合、推定に使用される異なる仕様を提供できます。

漸近分散/共分散行列は、適合した分布 `d` に対して計算することも、サンプル `c` と適合した分布 `d` を使用して推定することもできます。

引数 `biasCorr` は、潜在的なバイアスを修正するために推定で使用された方法を指定します。

適合した分布 `d` が連続であり、サンプルが提供されていない場合、計算は [Expectations.jl パッケージ](https://github.com/QuantEcon/Expectations.jl) を使用した期待値の数値評価に依存します。数値積分の精度は、デフォルト `n = 1000` の追加キーワード引数 `n` によって制御されます。

# 例

```julia
d = Poisson(10)
x = rand(d, 200)
spec = Huber(1.5)
λ = Mfit(x, d, spec)
dFit = Poisson(λ)

AVar(dFit, spec, :L)
AVar(x, dFit, spec, :L)

d = Normal(0, 1)
x = rand(d, 200)
spec = [Huber(1.5), Huber(2.5)]
ests = Mfit(x, d, spec)
dFit = NewDist(d, ests)

AVar(dFit, spec, :L, n = 500)
AVar(x, dFit, spec, :L)
```

理論的背景については [Stefanski and Book (2002)](https://www.jstor.org/stable/3087324) を参照してください。
