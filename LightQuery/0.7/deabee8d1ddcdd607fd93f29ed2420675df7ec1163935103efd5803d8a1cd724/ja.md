```
index(unindexed, key_function)
```

`unindexed`を`key_function`の結果でインデックスします。`key_function`の結果は一意でなければなりません。

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> result = @inferred index([-2, 1], abs)
LightQuery.Indexed{Int64,Int64,Array{Int64,1},Dict{Int64,Int64}} with 2 entries:
  2 => -2
  1 => 1

julia> @inferred result[2]
-2
```
