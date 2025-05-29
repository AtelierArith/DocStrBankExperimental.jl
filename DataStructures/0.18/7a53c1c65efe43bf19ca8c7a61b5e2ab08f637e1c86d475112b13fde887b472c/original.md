```
dequeue_pair!(pq)
```

Remove and return a the lowest priority key and value from a priority queue as a pair.

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
