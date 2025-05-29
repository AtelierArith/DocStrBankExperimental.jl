```
generate_gaussian_data(N::Int64, D::Int64, K::Int64,MixtureVar::Number)
```

`K` 個の `D` 次元のガウス分布から生成された `N` 個の観測値を生成します。ガウスの平均は、平均 `0` および分散 `MixtureVar` の `Normal` 分布からサンプリングされます。

`(Samples, Labels, Clusters_means, Clusters_cov)` を返します。

# 例

```julia
julia> x,y,clusters = generate_gaussian_data(10000,2,6,100.0)
[3644, 2880, 119, 154, 33, 3170]
...
```
