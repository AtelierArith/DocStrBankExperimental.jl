```
UnequalVarianceTTestElementWise(d1::UncertainDataset, d2::UncertainDataset,
    n::Int = 1000; μ0::Real = 0) -> Vector{UnequalVarianceTTest}
```

2つのサンプル `s1[i]` と `s2[i]` を考えます。各サンプルは、それぞれ不確実な値 `d1[i]` と `d2[i]` を提供する分布からの `n` 回のランダム抽出で構成されています。この関数は、ペア `(s1[i], s2[i])` に対して要素ごとの `EqualVarianceTTest` を実行します。具体的には：

帰無仮説 `s1[i]` と `s2[i]` が等しい平均を持つ分布から来ているという仮説に対して、分布が異なる平均を持つという対立仮説に基づくペアワイズの不均一分散二標本t検定を実施します。

この検定は、ウェルチのt検定として知られることがあります。等分散t検定とは異なり、ウェルチ-サッタースウェイトの方程式を使用して検定の自由度を計算します：

$$
    ν_{χ'} ≈ \frac{\left(\sum_{i=1}^n k_i s_i^2\right)^2}{\sum_{i=1}^n
        \frac{(k_i s_i^2)^2}{ν_i}}
$$
