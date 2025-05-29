```
distance_to_set(distance_definition, v, s)
```

値と集合との距離を計算します。`v ∈ s` の場合、距離はゼロです（またはすべての個々の距離がゼロです）。

各集合 `S` は、メンバーの適切な型の `T` を持つ `distance_to_set(d::DefaultDistance, v::T, s::S)` を少なくとも実装しています。
