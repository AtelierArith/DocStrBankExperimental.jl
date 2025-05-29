```
sampler(r::NominalRange, probs::AbstractVector{<:Real})
sampler(r::NominalRange)
sampler(r::NumericRange{T}, d)
```

`ParamRange`オブジェクト`r`（1次元範囲）からランダムサンプルを生成するために使用できるオブジェクト`s`を次のいずれかの呼び出しを使用して構築します：

```julia
rand(s)             # 1つのサンプル用
rand(s, n)          # n個のサンプル用
rand(rng, s [, n])  # RNGを指定するために
```

引数`probs`は、`r.values`と同じ長さの任意の確率ベクトルであることができます。上記の2番目の`sampler`メソッドは、均一な`probs`ベクトルを使用して最初のメソッドを呼び出します。

引数`d`は、Distributions.jlパッケージの`UnivariateDistribution`の任意のインスタンス、または`fit(d, ::NumericRange)`が定義されているDistributions.jlの*型*のいずれかであることができます。これには、`Arcsine`、`Uniform`、`Biweight`、`Cosine`、`Epanechnikov`、`SymTriangularDist`、`Triweight`、`Normal`、`Gamma`、`InverseGaussian`、`Logistic`、`LogNormal`、`Cauchy`、`Gumbel`、`Laplace`、および`Poisson`が含まれますが、最新のリストについては[`Distributions.fit`](@ref)のドキュメント文字列を参照してください。

`d`が*インスタンス*である場合、サンプリングは提供された分布`d`の切り取られた形式から行われ、切り取りの境界は`r.lower`と`r.upper`です（属性`r.origin`と`r.unit`の属性は無視されます）。離散数値範囲（`T <: Integer`）の場合、サンプルは丸められます。

`d`が*型*である場合、`Distributions.fit(d, r)`を使用して適切に切り取られた分布が自動的に生成されます。

*重要。* 値は`r.scale`に関係なく生成されますが、特別な場合として`r.scale`が呼び出し可能なオブジェクト`f`である場合があります。その場合、`f`は上記のように`rand`によって生成されたすべての値に適用されます（離散数値範囲の場合は丸める前に）。

### 例

```julia-repl
julia> r = range(Char, :letter, values=collect("abc"))
julia> s = sampler(r, [0.1, 0.2, 0.7])
julia> samples =  rand(s, 1000);
julia> StatsBase.countmap(samples)
Dict{Char,Int64} with 3 entries:
  'a' => 107
  'b' => 205
  'c' => 688

julia> r = range(Int, :k, lower=2, upper=6) # 数値だが離散
julia> s = sampler(r, Normal)
julia> samples = rand(s, 1000);
julia> UnicodePlots.histogram(samples)
           ┌                                        ┐
[2.0, 2.5) ┤▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 119
[2.5, 3.0) ┤ 0
[3.0, 3.5) ┤▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 296
[3.5, 4.0) ┤ 0
[4.0, 4.5) ┤▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 275
[4.5, 5.0) ┤ 0
[5.0, 5.5) ┤▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 221
[5.5, 6.0) ┤ 0
[6.0, 6.5) ┤▇▇▇▇▇▇▇▇▇▇▇ 89
           └                                        ┘
```
