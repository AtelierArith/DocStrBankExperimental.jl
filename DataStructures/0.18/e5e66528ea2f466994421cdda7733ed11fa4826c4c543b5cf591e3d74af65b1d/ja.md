```
PriorityQueue{K, V}([ord])
```

新しい [`PriorityQueue`](@ref) を構築します。キーの型は `K`、値/優先度の型は `V` です。順序が指定されていない場合、優先度キューは `V` のデフォルト比較を使用して最小順序になります。

`PriorityQueue` は `Dict` のように動作し、値をその優先度にマッピングしますが、最低優先度の要素を削除するための `dequeue!` 関数が追加されています。

```jldoctest
julia> PriorityQueue(Base.Order.Forward, "a" => 2, "b" => 3, "c" => 1)
PriorityQueue{String, Int64, Base.Order.ForwardOrdering} with 3 entries:
  "c" => 1
  "a" => 2
  "b" => 3
```
