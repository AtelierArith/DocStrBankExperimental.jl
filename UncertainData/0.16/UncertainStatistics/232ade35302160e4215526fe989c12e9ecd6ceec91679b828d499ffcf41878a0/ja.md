```
ApproximateTwoSampleKSTest(d1::AbstractUncertainValue,
    d2::AbstractUncertainValue, n::Int = 1000) -> ApproximateTwoSampleKSTest
```

不確実な値 `d1` を提供する分布が、不確実な値 `d2` を提供する分布と同じ分布であるという帰無仮説に対して、提供される分布が異なるという対立仮説に基づいて漸近的な二標本コルモゴロフ–スミルノフ検定を実行します。
