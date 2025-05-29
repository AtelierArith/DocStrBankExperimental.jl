```
struct AccumulatingEmissions <: Accumulating
```

`StorageBehavior`は、戦略的な期間内のすべての流入を蓄積します。`AccumulatingEmissions`は、捕捉された排出量を保存するためのソフト制約を表すために、[`ResourceEmit`](@ref) 排出ポイントとしても機能します。
