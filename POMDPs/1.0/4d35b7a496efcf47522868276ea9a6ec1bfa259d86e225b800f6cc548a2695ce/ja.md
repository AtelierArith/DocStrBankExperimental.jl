```
convert_a(::Type{V}, a, problem::Union{MDP,POMDP}) where V<:AbstractArray
convert_a(::Type{A}, vec::V, problem::Union{MDP,POMDP}) where {A,V<:AbstractArray}
```

アクションをベクトル化された形式に変換するか、その逆を行います。
