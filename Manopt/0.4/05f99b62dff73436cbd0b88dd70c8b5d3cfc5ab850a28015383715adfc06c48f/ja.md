```
StopWhenCostNaN <: StoppingCriterion
```

最適化問題のコスト関数を [`AbstractManoptProblem`](@ref) 内から見なくなる、すなわち `get_cost(p,get_iterate(o))`。

# コンストラクタ

```
StopWhenCostNaN()
```

停止基準をNaNに初期化します。
