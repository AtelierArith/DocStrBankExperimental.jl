```
AmplitudeAwareOrdinalPatterns <: OutcomeSpace
AmplitudeAwareOrdinalPatterns{m}(τ = 1, A = 0.5, lt = ComplexityMeasures.isless_rand)
```

[`OrdinalPatterns`](@ref) の変種で、振幅に関する情報も組み込まれています。これは、振幅に配慮した置換エントロピー [Azami2016](@cite) に基づいています。結果空間と引数は、[`OrdinalPatterns`](@ref) と同じです。

## 説明

[`WeightedOrdinalPatterns`](@ref) と同様に、各状態（または遅延）ベクトル $\mathbf{x}_i = (x_1^i, x_2^i, \ldots, x_m^i)$ から抽出された各順序パターンに重み $w_i$ が付けられます。

$$
w_i = \dfrac{A}{m} \sum_{k=1}^m |x_k^i | + \dfrac{1-A}{d-1}
\sum_{k=2}^d |x_{k}^i - x_{k-1}^i|,
$$

ここで $0 \leq A \leq 1$ です。$A=0$ の場合、$\mathbf{x}_i$ の要素間の内部差のみが重み付けされます。$A=1$ の場合、状態ベクトル要素の平均振幅のみが重み付けされます。$0<A<1$ の場合、組み合わせた重み付けが使用されます。
