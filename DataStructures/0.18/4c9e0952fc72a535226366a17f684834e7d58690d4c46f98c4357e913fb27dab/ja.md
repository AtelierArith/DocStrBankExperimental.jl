```
delete!(collection, key)
```

指定されたキーのマッピングをコレクションから削除し、コレクションを返します。

# 例

```jldoctest
julia> d = OrderedRobinDict("a"=>1, "b"=>2)
OrderedRobinDict{String, Int64} with 2 entries:
  "a" => 1
  "b" => 2

julia> delete!(d, "b")
OrderedRobinDict{String, Int64} with 1 entry:
  "a" => 1
```
