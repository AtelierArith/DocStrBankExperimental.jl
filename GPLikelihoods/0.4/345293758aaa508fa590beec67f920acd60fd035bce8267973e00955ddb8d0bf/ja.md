```
NegativeBinomialLikelihood(param::NBParam, invlink::Union{Function,Link})
```

ネガティブバイノミアル尤度のための多くの可能なパラメータ化があります。私たちは、[^\Hilbe'11]のp.137に記載された慣例に従い、いくつかの一般的なパラメータ化を提供します。`NegativeBinomialLikelihood`は特別な構造を持っており、最初の型パラメータ`NBParam`は潜在関数がどのパラメータ化で使用されるかを定義し、他の（スカラー）パラメータを含みます。`NBParam`自体には2つのサブタイプがあります：

  * `NBParamProb`：ここでは`f -> p`、すなわちベルヌーイ事象の成功の確率
  * `NBParamMean`：ここでは`f -> μ`、すなわち期待されるイベントの数

## `NBParam`の事前定義された型

### `NBParamProb`型で`p = invlink(f)`は成功または失敗の確率

  * [`NBParamSuccess`](@ref)：ここで`p = invlink(f)`は成功の確率です。これは[`Distributions.jl`](https://juliastats.org/Distributions.jl/latest/univariate/#Distributions.NegativeBinomial)で使用される定義です。
  * [`NBParamFailure`](@ref)：ここで`p = invlink(f)`は失敗の確率です。

### `NBParamMean`型で`μ = invlink(f)`は平均/期待されるイベントの数

  * [`NBParamI`](@ref)：平均は`f`にリンクされ、分散は`μ(1 + α)`で与えられます。
  * [`NBParamII`](@ref)：平均は`f`にリンクされ、分散は`μ(1 + α * μ)`で与えられます。
  * [`NBParamPower`](@ref)：平均は`f`にリンクされ、分散は`μ(1 + α * μ^ρ)`で与えられます。

新しいパラメータ化を作成するには、次の手順が必要です：

  * 新しい型`struct MyNBParam{T} <: NBParam; myparams::T; end`を作成します。
  * `(l::NegativeBinomialLikelihood{<:MyNBParam})(f::Real)`をディスパッチし、これは[`NegativeBinomial`](https://juliastats.org/Distributions.jl/latest/univariate/#Distributions.NegativeBinomial)を`Distributions.jl`から返さなければなりません。

`NegativeBinomial`は[`NBParamSuccess`](@ref)のパラメータ化に従い、すなわち最初の引数は成功の数で、2番目の引数は成功の確率です。

## 例

```julia-repl
julia> NegativeBinomialLikelihood(NBParamSuccess(10), logistic)(2.0)
NegativeBinomial{Float64}(r=10.0, p=0.8807970779778824)
julia> NegativeBinomialLikelihood(NBParamFailure(10), logistic)(2.0)
NegativeBinomial{Float64}(r=10.0, p=0.11920292202211757)

julia> d = NegativeBinomialLikelihood(NBParamI(3.0), exp)(2.0)
NegativeBinomial{Float64}(r=2.4630186996435506, p=0.25)
julia> mean(d) ≈ exp(2.0)
true
julia> var(d) ≈ exp(2.0) * (1 + 3.0)
true
```

[^Hilbe'11]: Hilbe, Joseph M. Negative binomial regression. Cambridge University Press, 2011.
