```
enqueue!(pq, k=>v)
```

優先キュー `pq` に優先度 `v` でキー `k` を挿入します。

```jldoctest
julia> a = PriorityQueue(PriorityQueue("a"=>1, "b"=>2, "c"=>3))
PriorityQueue{String, Int64, Base.Order.ForwardOrdering} with 3 entries:
  "a" => 1
  "b" => 2
  "c" => 3

julia> enqueue!(a, "d"=>4)
PriorityQueue{String, Int64, Base.Order.ForwardOrdering} with 4 entries:
  "a" => 1
  "b" => 2
  "c" => 3
  "d" => 4
```
