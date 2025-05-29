```
OneSampleTTest(d1::AbstractUncertainValue,
                d2::AbstractUncertainValue,
                n::Int = 1000; μ0::Real=0) -> OneSampleTTest
```

`d1` と `d2` の不確実な値のペア間の差が平均 `μ0` を持つ分布から来ているという帰無仮説に対して、分布が平均 `μ0` を持たないという対立仮説のもとで対応のあるサンプルt検定を実施します。
