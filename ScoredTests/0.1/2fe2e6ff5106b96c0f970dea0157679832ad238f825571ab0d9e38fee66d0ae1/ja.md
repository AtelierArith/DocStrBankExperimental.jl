```
ScoredTestSet([description])
```

[`ScoredTest`](@ref)と[`ScoredTestSet`](@ref)のコレクション。

新しいテストやテストセットを追加するには、`*=` 演算子を使用します。例えば、

```julia
ts2 = ScoredTestSet("テストのサブグループ")
ts2 *= @scoredtest π < 3
ts2 *= @scoredtest π ≈ 3.1415

ts = ScoredTestSet("メイングループ")
ts *= @scoredtest 1 + 1 == 2
ts *= ts2
```
