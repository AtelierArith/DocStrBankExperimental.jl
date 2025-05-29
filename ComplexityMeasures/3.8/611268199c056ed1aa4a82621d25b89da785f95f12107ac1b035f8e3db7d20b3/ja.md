```
probabilities(
    [est::ProbabilitiesEstimator], o::OutcomeSpace, x::Array_or_SSSet
) → p::Probabilities
```

[`probabilities_and_outcomes`](@ref) 関数と同じ確率を計算しますが、2つの違いがあります：

1. 結果を明示的に返さない。
2. 結果がカウントを推定する際に無料で推定されない場合、結果を列挙するために特別な整数型が使用され、結果を推定する計算コストを回避します。

```
probabilities([est::ProbabilitiesEstimator], counts::Counts) → (p::Probabilities, Ω)
```

上記と同じですが、[`Counts`](@ref) のセットから直接確率を推定します。
