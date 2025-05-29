```
UnequalVarianceTTestPooled(d1::UncertainDataset, d2::UncertainDataset,
    n::Int = 1000; μ0::Real = 0) -> UnequalVarianceTTest
```

2つのサンプル `s1[i]` と `s2[i]` を考えます。各サンプルは、それぞれ不確実な値 `d1[i]` と `d2[i]` を提供する分布からの `n` 回のランダム抽出で構成されています。すべての `s1[i]` をプールサンプル `S1` に、すべての `s2[i]` をプールサンプル `S2` に集めます。

この関数は、プールサンプル `S1` と `S2` が平均が等しい分布から来ているという帰無仮説に対して、分布が異なる平均を持つという対立仮説の下で不等分散の二標本t検定を実行します。
