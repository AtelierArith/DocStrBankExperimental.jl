```
continuous_events(sys::AbstractSystem)::Vector{SymbolicContinuousCallback}
```

抽象システムおよびその構成サブシステム内のすべての `continuous_events` のベクターを返します。返されたベクター内の `SymbolicContinuousCallback` は、イベントを定義するために使用される `Pair` の最初と2番目の要素に対応する `eqs` と `affect` の2つのフィールドを持つ構造体です。すなわち、`eqs => affect` です。
