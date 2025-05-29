```
ConstantSamplesRoundingMode(start::RoundingMode)
```

[`AlignedSpan`](@ref) のための丸めオブジェクトを作成し、`span` の `start` と `duration` によって `AlignedSpan` が構築されるべきであることを示しますが、その `stop` は考慮しません。

もし二つの `span` が同じ duration を持つ場合、この丸めモードで構築された結果の `AlignedSpan` は同じ数のサンプルを持ちます。

さらに [`AlignedSpan(sample_rate, span, mode::ConstantSamplesRoundingMode)`](@ref) を参照してください。
