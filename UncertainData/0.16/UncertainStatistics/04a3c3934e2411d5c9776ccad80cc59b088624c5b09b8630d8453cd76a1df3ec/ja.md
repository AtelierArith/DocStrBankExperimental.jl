```
UnequalVarianceTTest(d1::AbstractUncertainValue, d2::AbstractUncertainValue,
    n::Int = 1000; μ0::Real = 0) -> UnequalVarianceTTest
```

2つのサンプル `s1` と `s2` を考えます。それぞれは、分布 `d1` と `d2` からの `n` 回のランダム抽出から成ります。

帰無仮説 `s1` と `s2` が等しい平均を持つ分布から来ているということに対して、分布が異なる平均を持つという対立仮説に基づいて、不等分散の二標本t検定を実施します。
