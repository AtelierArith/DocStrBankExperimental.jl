```
counts(o::OutcomeSpace, x) → cts::Counts
```

[`counts_and_outcomes`](@ref) 関数と同じカウントを計算しますが、2つの違いがあります。

1. 結果を明示的に返さない。
2. カウントを推定する際に結果が無料で推定されない場合、結果を列挙するために特別な整数型が使用され、結果を推定する計算コストを回避します。
