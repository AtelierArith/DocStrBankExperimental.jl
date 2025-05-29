```
OneSampleTTest(d::AbstractUncertainValue, n::Int = 1000;
    μ0::Real = 0) -> OneSampleTTest
```

不確実な値が平均 `μ0` を持つ分布を持つという帰無仮説に対して、分布が平均 `μ0` を持たないという対立仮説の一標本t検定を実行します。`n` はリサンプリング中の引き数の数を示します。
