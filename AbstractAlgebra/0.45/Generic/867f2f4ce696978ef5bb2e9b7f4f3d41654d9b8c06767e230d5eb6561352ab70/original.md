```
push!(pq::PriorityQueue{K,V}, pair::Pair{K,V}) where {K,V}
```

Insert the a key `k` into a priority queue `pq` with priority `v`.

# Examples

```jldoctest
julia> a = Generic.PriorityQueue("a" => 1, "b" => 2, "c" => 3, "e" => 5)
AbstractAlgebra.Generic.PriorityQueue{String, Int64, Base.Order.ForwardOrdering} with 4 entries:
  "a" => 1
  "b" => 2
  "c" => 3
  "e" => 5

julia> push!(a, "d" => 4)
AbstractAlgebra.Generic.PriorityQueue{String, Int64, Base.Order.ForwardOrdering} with 5 entries:
  "a" => 1
  "b" => 2
  "c" => 3
  "d" => 4
  "e" => 5
```
