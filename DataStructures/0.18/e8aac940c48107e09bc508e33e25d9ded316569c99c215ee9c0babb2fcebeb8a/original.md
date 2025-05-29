```
enqueue!(pq, k=>v)
```

Insert the a key `k` into a priority queue `pq` with priority `v`.

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
