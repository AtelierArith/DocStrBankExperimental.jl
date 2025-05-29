```
SimHistory
```

`simulate(::HistoryRecorder, ::Union{MDP,POMDP},...)` によって返される (PO)MDP シミュレーション履歴。

これは、状態、アクションなどを含む [`NamedTuples`](https://docs.julialang.org/en/v1/manual/types/index.html#Named-Tuple-Types-1) の `AbstractVector` です。

# 例

```
hist[1][:s] # 履歴の最初の状態を返します
```

```
hist[:a] # 履歴のすべてのアクションを返します
```
