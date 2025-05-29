```
StoppingCriterionGroup <: StoppingCriterion
```

停止基準のセットで構成される停止基準の抽象型です。合計でそれ自体が停止基準として機能します。例としては、停止基準を組み合わせるために使用できる[`StopWhenAny`](@ref)や[`StopWhenAll`](@ref)があります。
