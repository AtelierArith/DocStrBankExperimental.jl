```
index(unindexed, key_function)
```

Index `unindexed` by the results of `key_function`. Results of `key_function` must be unique.

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
