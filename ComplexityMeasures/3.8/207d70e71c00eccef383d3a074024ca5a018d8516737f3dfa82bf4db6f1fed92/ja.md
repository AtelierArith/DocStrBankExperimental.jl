```
allprobabilities_and_outcomes(est::ProbabilitiesEstimator, x::Array_or_SSSet) → (p::Probabilities, outs)
allprobabilities_and_outcomes(o::OutcomeSpace, x::Array_or_SSSet) → (p::Probabilities, outs)
```

[`probabilities_and_outcomes`](@ref)と同様ですが、確率が`0`の結果が返されるベクターに明示的に追加されることを保証します。これは、`p[i]`が`ospace[i]`の確率であり、`ospace =`[`outcome_space`](@ref)`(est, x)`であることを意味します。

この関数は、同じ推定器の下で異なる入力データ`x, y`の確率質量関数を比較したい場合に便利です。例えば、2つのPMFのKLダイバージェンスを計算するには、同じインデックスを遵守している必要があります。これは、`est`が同じであっても`0`エントリをスキップするため、[`probabilities`](@ref)には当てはまりませんが、[`allprobabilities_and_outcomes`](@ref)には当てはまります。
