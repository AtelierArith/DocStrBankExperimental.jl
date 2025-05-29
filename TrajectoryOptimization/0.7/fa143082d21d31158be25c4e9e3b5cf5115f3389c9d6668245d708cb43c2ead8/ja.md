```
Objective{C}
```

目的: ステージコストと終端コスト関数を格納します。各時間ステップでのすべてのコスト関数は同じタイプでなければなりません。

コンストラクタ:

```
Objective(cost, N)
Objective(cost, cost_term, N)
Objective(costs::Vector{<:CostFunction}, cost_term)
Objective(costs::Vector{<:CostFunction})
```
