```
partitions(s::AbstractVector, m::Int)
```

配列 `s` の要素を正確に `m` 個の部分集合に分割するすべての集合分割を生成します。これは配列の配列として表されます。分割の数は非常に大きくなる可能性があるため、この関数はイテレータオブジェクトを返します。すべての分割の配列を取得するには `collect(partitions(s, m))` を使用します。`m` 個の部分集合への分割の数は第二種スターリング数に等しく、`length(partitions(s, m))` を使用して効率的に計算できます。
