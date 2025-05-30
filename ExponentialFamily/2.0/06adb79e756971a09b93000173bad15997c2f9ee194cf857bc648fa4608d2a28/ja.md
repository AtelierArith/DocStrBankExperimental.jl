```
ExponentialFamilyDistribution(::Type{T}, naturalparameters, conditioner, attributes)
```

`ExponentialFamilyDistribution` 構造体は、自然パラメータ化における一般的な指数族分布を表します。型 `T` は、分布型（例：`Distributions.jl` パッケージから）または変量型（例：`Univariate`）のいずれかです。このパッケージの文脈では、指数族分布は次の形で表されます：

$$
pₓ(x ∣ η) = h(x) ⋅ exp[ η ⋅ T(x) - A(η) ]
$$

ここで：

  * `h(x)` は基準測度です。
  * `T(x)` は十分統計量を表します。
  * `A(η)` は対数分配関数を表します。
  * `η` は自然パラメータを示します。

指数族の特定のメンバーに対して：

  * `getattributes` は `nothing` または `ExponentialFamilyDistributionAttributes` のいずれかを返します。
  * `getbasemeasure` は正の値を持つ関数を返します。
  * `getsufficientstatistics` は [x, x^2] や [x, logx] のような関数の反復可能な集合を返します。
  * `getnaturalparameters` は自然パラメータの値を保持する反復可能な集合を返します。
  * `getlogpartition` は自然パラメータに依存する関数を返し、分布が1に正規化されることを保証します。
  * `getsupport` は分布が定義されている集合を返します。実数、正の整数、3次元立方体などが考えられます。値がサポートに属するかどうかを確認するには、`∈` 演算子または `insupport()` 関数を使用します。

!!! note
    `attributes` は `nothing` である可能性があります。この場合、パッケージは型 `T` から対応する属性を導出しようとします。


```jldoctest
julia> ef = convert(ExponentialFamilyDistribution, Bernoulli(0.5))
ExponentialFamily(Bernoulli)

julia> getsufficientstatistics(ef)
(identity,)
```

```jldoctest
julia> ef = convert(ExponentialFamilyDistribution, Laplace(1.0, 0.5))
ExponentialFamily(Laplace, conditioned on 1.0)

julia> logpdf(ef, 4.0)
-6.0
```

参照： [`getbasemeasure`](@ref), [`getsufficientstatistics`](@ref), [`getnaturalparameters`](@ref), [`getlogpartition`](@ref), [`getsupport`](@ref)
