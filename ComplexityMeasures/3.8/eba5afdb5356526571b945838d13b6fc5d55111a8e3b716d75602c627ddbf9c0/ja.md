```
information_normalized([e::DiscreteInfoEstimator,] [est::ProbabilitiesEstimator,] o::OutcomeSpace, x) → h::Real
```

与えられた離散情報測度の正規化されたバージョンを推定します。これは、[`information`](@ref) の値を `o` に対して与えられた最大可能値で割ったものです。

[`information`](@ref) と同じ便利な構文がここでも使用できます。

`information_normalized(e::DiscreteInfoEstimator, probs::Probabilities)` というメソッドは存在しないことに注意してください。なぜなら、`probs` から *可能な* 結果の数（すなわち、[`total_outcomes`](@ref)）を知る方法がないからです。

## 正規化された値

[`PlugIn`](@ref) 推定器の場合、`h̃ ∈ [0, 1]` が保証されます。他の推定器については、推定器が過剰に修正する可能性があるため、これを保証することはできません。正規化された値を推定するために [`PlugIn`](@ref) 以外のものを使用する場合は、自分が何をしているのかを理解している必要があります。
