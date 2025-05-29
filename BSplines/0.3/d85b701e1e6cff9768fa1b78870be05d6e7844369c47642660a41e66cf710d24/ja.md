```
averagebasis(order, datapoints) -> BSplineBasis
```

指定された `order` のBスプライン基底を返し、与えられた `datapoints` に対する補間に適しています。`datapoints` ベクトルはソートされていると仮定されます。

計算されたブレークポイントは、最適なブレークポイントシーケンスに対する「合理的な代替」として [^deBoor1978] の219ページに記載されており、「しばしば最適に非常に近い」ものであり、計算コストが低いです。

[^deBoor1978]: Carl de Boor, *A Practical Guide to Splines*, New York, N.Y.: Springer, 1978.

# 例

```jldoctest
julia> averagebasis(5, 0:10)
11-element BSplines.BSplineBasis{Vector{Float64}}:
 order: 5
 breakpoints: [0.0, 2.5, 3.5, 4.5, 5.5, 6.5, 7.5, 10.0]
```
