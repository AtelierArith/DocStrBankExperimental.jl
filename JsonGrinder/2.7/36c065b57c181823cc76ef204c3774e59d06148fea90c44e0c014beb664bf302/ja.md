```
map_keys(f, d)
```

呼び出し可能な `f` によってすべてのキーが（再帰的に）変換された新しいドキュメントを返します。

# 例

```jldoctest
julia> d = Dict("a" => 1, "b" => Dict("c" => "foo"))
Dict{String, Any} with 2 entries:
  "b" => Dict("c"=>"foo")
  "a" => 1

julia> map_keys(Symbol, d)
Dict{Symbol, Any} with 2 entries:
  :a => 1
  :b => Dict(:c=>"foo")

julia> map_keys(string, d)
Dict{String, Any} with 2 entries:
  "b" => Dict("c"=>"foo")
  "a" => 1
```
