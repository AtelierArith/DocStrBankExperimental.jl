```
groupview([by], container)
```

`group`と似ていますが、各グループはインデックス可能な入力`container`の`view`です。

# 例

```jldoctest
julia> v = [3,4,2,6,5,8]
6-element Array{Int64,1}:
 3
 4
 2
 6
 5
 8

julia> groups = groupview(iseven, v)
2-element GroupDictionary{Bool,SubArray{Int64,1,Array{Int64,1},Tuple{Array{Int64,1}},false},Array{Int64,1},Dictionary{Bool,Array{Int64,1}}}
 false │ [3, 5]
  true │ [4, 2, 6, 8]

julia> groups[false] .= 99  # 奇数の値をすべて99に設定
2-element view(::Array{Int64,1}, [1, 5]) with eltype Int64:
 99
 99

julia> v
6-element Array{Int64,1}:
 99
  4
  2
  6
 99
  8
```
