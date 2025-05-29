```
OrderStatistic{D<:UnivariateDistribution,S<:ValueSupport} <: UnivariateDistribution{S}
```

独立同分布のサンプルからの順序統計量の分布。

```
OrderStatistic(dist::UnivariateDistribution, n::Int, rank::Int; check_args::Bool=true)
```

`dist`からの$n$個の独立サンプルの`rank` $=i$番目の順序統計量の分布を構築します。

サンプルの$i$番目の順序統計量は、ソートされたサンプルの$i$番目の要素です。例えば、1番目の順序統計量はサンプルの最小値であり、$n$番目の順序統計量はサンプルの最大値です。

もし$f$が`dist`の確率密度（質量）関数で、分布関数を$F$とすると、連続`dist`の順序統計量の確率密度関数$g$は次のようになります。

$$
g(x; n, i) = {n \choose i} [F(x)]^{i-1} [1 - F(x)]^{n-i} f(x),
$$

また、離散`dist`の順序統計量の確率質量関数$g$は次のようになります。

$$
g(x; n, i) = \sum_{k=i}^n {n \choose k} \left( [F(x)]^k [1 - F(x)]^{n-k} - [F(x_-)]^k [1 - F(x_-)]^{n-k} \right),
$$

ここで、$x_-$は$x$より小さい`dist`のサポート内の最大の要素です。

順序統計量の部分集合の同時分布については、[`JointOrderStatistics`](@ref)を使用してください。

## 例

```julia
OrderStatistic(Cauchy(), 10, 1)              # サンプルの最小値の分布
OrderStatistic(DiscreteUniform(10), 10, 10)  # サンプルの最大値の分布
OrderStatistic(Gamma(1, 1), 11, 5)           # サンプルの中央値の分布
```
