```
MixtureIntervalProbabilities{N, P <: OrthogonalIntervalProbabilities, Q <: IntervalProbabilities}
```

独立した遷移確率の混合に対する `OrthogonalIntervalProbabilities` のタプルで、すべてが同じソース/アクションペアとターゲット状態を共有します。混合内の各モデルの遷移確率の構造についての詳細は、[OrthogonalIntervalProbabilities](@ref)を参照してください。この混合は、`weighting_probs` と呼ばれる `IntervalProbabilities` の曖昧さセットによって重み付けされています。

### フィールド

  * `mixture_probs::NTuple{N, P}`: 各軸に沿った `OrthogonalIntervalProbabilities` 遷移確率のタプル。
  * `weighting_probs::Q`: 混合のための重み付け曖昧さセット。

### 例

以下は、1次元の2つの `OrthogonalIntervalProbabilities` の混合の簡単な例で、同じソース/アクションペアとターゲット状態、および重み付け曖昧さセットを持っています。

```jldoctest
prob1 = OrthogonalIntervalProbabilities(
    (
        IntervalProbabilities(;
            lower = [
                0.0 0.5
                0.1 0.3
                0.2 0.1
            ],
            upper = [
                0.5 0.7
                0.6 0.5
                0.7 0.3
            ],
        ),
    ),
    (Int32(2),),
)
prob2 = OrthogonalIntervalProbabilities(
    (
        IntervalProbabilities(;
            lower = [
                0.1 0.4
                0.2 0.2
                0.3 0.0
            ],
            upper = [
                0.4 0.6
                0.5 0.4
                0.6 0.2
            ],
        ),
    ),
    (Int32(2),),
)
weighting_probs = IntervalProbabilities(; lower = [
    0.3 0.5
    0.4 0.3
], upper = [
    0.8 0.7
    0.7 0.5
])
mixture_prob = MixtureIntervalProbabilities((prob1, prob2), weighting_probs)
```
