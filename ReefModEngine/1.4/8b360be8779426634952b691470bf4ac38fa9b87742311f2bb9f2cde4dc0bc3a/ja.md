```
match_id(id::String)::Int64
match_ids(ids::Vector{String})::Vector{Int64}
```

与えられたIDに対して、ReefMod Engineのリーフリストに基づいて一致するインデックス位置を見つけます。

# 注意

ReefMod Engineのリーフリストはすべて大文字です。提供されたIDは一致を確保するために大文字に変換されます。

# 例

```julia
julia> reef_ids()
# 3806-element Vector{String}:
#  "10-330"
#  "10-331"
#  ⋮
#  "23-048"
#  "23-049"

julia> match_id("10-330")
#  1

julia> match_id("23-049")
#  3806

julia> match_ids(["23-048", "10-331"])
#  3805
#  2
```
