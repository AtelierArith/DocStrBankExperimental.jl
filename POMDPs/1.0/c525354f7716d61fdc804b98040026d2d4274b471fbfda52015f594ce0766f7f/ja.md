```
convert_o(::Type{V}, o, problem::Union{MDP,POMDP}) where V<:AbstractArray
convert_o(::Type{O}, vec::V, problem::Union{MDP,POMDP}) where {O,V<:AbstractArray}
```

観測をベクトル化された形式に変換するか、その逆を行います。
