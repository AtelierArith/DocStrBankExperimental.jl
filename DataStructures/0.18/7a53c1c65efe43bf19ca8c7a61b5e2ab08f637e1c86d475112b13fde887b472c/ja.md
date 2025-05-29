```
dequeue_pair!(pq)
```

優先キューから最低優先度のキーと値をペアとして削除して返します。

```jldoctest
julia> a = PriorityQueue(Base.Order.Forward, "a" => 2, "b" => 3, "c" => 1)
PriorityQueue{String, Int64, Base.Order.ForwardOrdering} with 3 entries:
  "c" => 1
  "a" => 2
  "b" => 3

julia> dequeue_pair!(a)
"c" => 1

julia> a
PriorityQueue{String, Int64, Base.Order.ForwardOrdering} with 2 entries:
  "a" => 2
  "b" => 3
```
