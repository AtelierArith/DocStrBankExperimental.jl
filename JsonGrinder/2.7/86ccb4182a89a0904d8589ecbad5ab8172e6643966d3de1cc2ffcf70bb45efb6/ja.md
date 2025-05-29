```
remove_nulls(js)
```

新しいドキュメントを返します。すべての `null` 値（julia では `nothing` として表される）が削除されます。

# 例

```jldoctest
julia> remove_nulls(Dict("a" => 1, "b" => nothing))
Dict{String, Union{Nothing, Int64}} with 1 entry:
  "a" => 1

julia> [nothing, Dict("a" => 1), nothing, Dict("a" => nothing)] |> remove_nulls
2-element Vector{Dict{String}}:
 Dict("a" => 1)
 Dict{String, Nothing}()
```
