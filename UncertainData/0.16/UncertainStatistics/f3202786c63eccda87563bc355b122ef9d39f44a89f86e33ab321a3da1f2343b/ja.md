```
EqualVarianceTTest(d1::AbstractUncertainValue, d2::AbstractUncertainValue,
    n::Int = 1000; μ0::Real = 0) -> EqualVarianceTTest
```

2つのサンプル `s1` と `s2` を考えます。それぞれは、分布 `d1` と `d2` からの `n` 回のランダム抽出から構成されています。

この関数は、`s1` と `s2` が平均と分散が等しい分布から来ているという帰無仮説に対して、分布が異なる平均を持つが分散は等しいという対立仮説の下での二標本t検定を実行します。
