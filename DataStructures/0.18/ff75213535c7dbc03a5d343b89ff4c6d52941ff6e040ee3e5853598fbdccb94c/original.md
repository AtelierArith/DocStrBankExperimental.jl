```
dequeue!(pq)
```

Remove and return the lowest priority key from a priority queue.

```jldoctest
julia> a = PriorityQueue(Base.Order.Forward, ["a" => 2, "b" => 3, "c" => 1])
PriorityQueue{String, Int64, Base.Order.ForwardOrdering} with 3 entries:
  "c" => 1
  "a" => 2
  "b" => 3

julia> dequeue!(a)
"c"

julia> a
PriorityQueue{String, Int64, Base.Order.ForwardOrdering} with 2 entries:
  "a" => 2
  "b" => 3
```
