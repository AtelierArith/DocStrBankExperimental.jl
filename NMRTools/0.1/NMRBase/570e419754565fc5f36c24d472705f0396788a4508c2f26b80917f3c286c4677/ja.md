```
MQ(coherences, label=="")
```

複数量子コヒーレンスの表現。コヒーレンスは、`(nucleus, coherenceorder)`の形式のタプルのタプルとして指定されます。

# 例

```jldoctest
julia> MQ(((H1,1), (C13,-1)), "ZQ")
MQ(((H1, 1), (C13, -1)), "ZQ")

julia> MQ(((H1,3), (C13,1)), "QQ")
MQ(((H1, 3), (C13, 1)), "QQ")
```

参照してください [`Nucleus`](@ref), [`SQ`](@ref).
