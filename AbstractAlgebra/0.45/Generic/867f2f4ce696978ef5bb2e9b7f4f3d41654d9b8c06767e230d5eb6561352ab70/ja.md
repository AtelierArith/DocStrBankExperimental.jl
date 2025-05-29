```
push!(pq::PriorityQueue{K,V}, pair::Pair{K,V}) where {K,V}
```

優先度 `v` で優先度キュー `pq` にキー `k` を挿入します。

# 例

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
