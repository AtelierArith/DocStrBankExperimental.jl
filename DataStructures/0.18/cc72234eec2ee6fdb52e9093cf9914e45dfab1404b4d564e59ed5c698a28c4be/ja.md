```
empty!(collection) -> collection
```

`collection`からすべての要素を削除します。

# 例

```jldoctest
julia> A = OrderedRobinDict("a" => 1, "b" => 2)
OrderedRobinDict{String, Int64} with 2 entries:
  "a" => 1
  "b" => 2

julia> empty!(A);

julia> A
OrderedRobinDict{String, Int64}()
```
