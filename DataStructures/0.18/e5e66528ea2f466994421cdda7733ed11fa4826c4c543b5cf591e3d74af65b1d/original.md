```
PriorityQueue{K, V}([ord])
```

Construct a new [`PriorityQueue`](@ref), with keys of type `K` and values/priorites of type `V`. If an order is not given, the priority queue is min-ordered using the default comparison for `V`.

A `PriorityQueue` acts like a `Dict`, mapping values to their priorities, with the addition of a `dequeue!` function to remove the lowest priority element.

```jldoctest
julia> PriorityQueue(Base.Order.Forward, "a" => 2, "b" => 3, "c" => 1)
PriorityQueue{String, Int64, Base.Order.ForwardOrdering} with 3 entries:
  "c" => 1
  "a" => 2
  "b" => 3
```
