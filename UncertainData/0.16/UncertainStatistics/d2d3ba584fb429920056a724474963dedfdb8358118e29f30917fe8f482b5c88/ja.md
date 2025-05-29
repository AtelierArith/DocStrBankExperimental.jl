```
ApproximateTwoSampleKSTestPooled(d1::UncertainDataset,
    d2::UncertainDataset, n::Int = 1000) -> ApproximateTwoSampleKSTest
```

まず、`d1`の各不確実な値から`n`の実現を引き出し、次に`d2`の各不確実な値から別々に`n`の実現を引き出します。次に、`d1`のすべての実現を一緒にプールし、`d2`のすべての実現を一緒にプールします。

プールされた実現に対して、`d1`の値プールを提供する分布が`d2`の値プールを提供する分布と同じであるという帰無仮説に対して、提供される分布が異なるという対立仮説を検定する漸近的二標本コルモゴロフ–スミルノフ検定を実施します。
