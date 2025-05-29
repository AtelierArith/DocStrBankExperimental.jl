```
StopWhenCostLess <: StoppingCriterion
```

最適化問題のコスト関数を見続けるのを停止する閾値を[`AbstractManoptProblem`](@ref)内に保存します。すなわち、`get_cost(p,get_iterate(o))`です。

# コンストラクタ

```
StopWhenCostLess(ε)
```

停止基準を閾値`ε`に初期化します。
