```
empty!(collection) -> collection
```

コレクションからすべての要素を削除します。

# 例

```jldoctest
julia> A = RobinDict("a" => 1, "b" => 2)
RobinDict{String, Int64} with 2 entries:
  "b" => 2
  "a" => 1

julia> empty!(A);

julia> A
RobinDict{String, Int64}()
```
