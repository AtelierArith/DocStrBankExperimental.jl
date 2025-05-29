```
OneSampleTTestElementWise(d1::UncertainDataset,
    d2::UncertainDataset,
    n::Int = 1000; μ0::Real = 0) -> Vector{OneSampleTTest}
```

不確実な値が平均 `μ0` を持つ分布を持つという帰無仮説に対して、その分布が平均 `μ0` を持たないという対立仮説の一標本t検定を実行します。

`n` はリサンプリング中の引き出しの数を示します。
