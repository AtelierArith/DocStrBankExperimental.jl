```
JointOrderStatistics <: ContinuousMultivariateDistribution
```

連続一変量分布からのサンプルの順序統計のサブセットの同時分布。

```
JointOrderStatistics(
    dist::ContinuousUnivariateDistribution,
    n::Int,
    ranks=Base.OneTo(n);
    check_args::Bool=true,
)
```

指定された `ranks` の順序統計の同時分布を、`dist` からのサイズ `n` のIIDサンプルに対して構築します。

サンプルの $i$ 番目の順序統計は、ソートされたサンプルの $i$ 番目の要素です。例えば、1番目の順序統計はサンプルの最小値であり、$n$ 番目の順序統計はサンプルの最大値です。

`ranks` は、1から `n` の間のユニークな `Int` のソートされたベクターまたはタプルでなければなりません。

単一の順序統計の場合は、[`OrderStatistic`](@ref) を代わりに使用してください。

## 例

```julia
JointOrderStatistics(Normal(), 10)           # Product(fill(Normal(), 10)) restricted to ordered vectors
JointOrderStatistics(Cauchy(), 10, 2:9)      # joint distribution of all but the extrema
JointOrderStatistics(Cauchy(), 10, (1, 10))  # joint distribution of only the extrema
```
