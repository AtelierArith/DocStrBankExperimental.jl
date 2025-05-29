```
EqualVarianceTTestElementWise(d1::UncertainDataset, d2::UncertainDataset,
    n::Int = 1000; μ0::Real = 0) -> Vector{EqualVarianceTTest}
```

2つのサンプル `s1[i]` と `s2[i]` を考えます。各サンプルは、それぞれ不確実な値 `d1[i]` と `d2[i]` を提供する分布からの `n` 回のランダム抽出で構成されています。この関数は、ペア `(s1[i], s2[i])` に対して要素ごとの `EqualVarianceTTest` を実行します。具体的には：

`s1[i]` と `s2[i]` が平均と分散が等しい分布から来ているという帰無仮説に対して、分布が異なる平均を持つが分散は等しいという対立仮説のもとで、ペアワイズの二標本t検定を実施します。
