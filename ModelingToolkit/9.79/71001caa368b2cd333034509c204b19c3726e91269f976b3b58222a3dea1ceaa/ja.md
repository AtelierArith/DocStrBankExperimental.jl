```
discrete_events(sys::AbstractSystem) :: Vector{SymbolicDiscreteCallback}
```

抽象システムおよびその構成サブシステム内のすべての `discrete_events` のベクターを返します。返されるベクター内の `SymbolicDiscreteCallback` は、イベントを定義するために使用される `Pair` の最初と2番目の要素に対応する `condition` と `affect` の2つのフィールドを持つ構造体です。すなわち、`condition => affect` です。
