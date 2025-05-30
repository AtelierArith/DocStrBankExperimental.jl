```
delete!(pq, key)
```

指定されたキーのマッピングを優先度キューから削除し、優先度キューを返します。

# 例

```jldoctest
julia> q = PriorityQueue(Base.Order.Forward, "a"=>2, "b"=>3, "c"=>1)
PriorityQueue{String, Int64, Base.Order.ForwardOrdering} with 3 entries:
  "c" => 1
  "a" => 2
  "b" => 3
julia> delete!(q, "b")
PriorityQueue{String,Int64,Base.Order.ForwardOrdering} with 2 entries:
  "c" => 1
  "a" => 2
```
