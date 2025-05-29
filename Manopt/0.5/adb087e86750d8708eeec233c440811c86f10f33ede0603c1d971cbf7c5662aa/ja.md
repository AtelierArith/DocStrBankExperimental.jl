```
StopWhenEvolutionStagnates{TParam<:Real} <: StoppingCriterion
```

各イテレーションでの最良および中央値のフィットネスは、最後の20%の間、ただし少なくとも `min_size` かつ最大で `max_size` のイテレーションで追跡されます。解法は、両方の履歴で最新の `fraction` の値の中央値が最も古い `fraction` よりも良くない場合に停止します。
