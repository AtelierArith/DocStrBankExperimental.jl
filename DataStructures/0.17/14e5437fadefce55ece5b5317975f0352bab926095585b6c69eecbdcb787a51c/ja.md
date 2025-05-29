```
delete!(collection, key)
```

指定されたキーのマッピングをコレクションから削除し、コレクションを返します。

# 例

```jldoctest
julia> d = RobinDict("a"=>1, "b"=>2)
RobinDict{String,Int64} with 2 entries:
  "b" => 2
  "a" => 1

julia> delete!(d, "b")
RobinDict{String,Int64} with 1 entry:
  "a" => 1
```
