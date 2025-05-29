```
convert_s(::Type{V}, s, problem::Union{MDP,POMDP}) where V<:AbstractArray
convert_s(::Type{S}, vec::V, problem::Union{MDP,POMDP}) where {S,V<:AbstractArray}
```

状態をベクトル化された形式に変換するか、その逆を行います。
