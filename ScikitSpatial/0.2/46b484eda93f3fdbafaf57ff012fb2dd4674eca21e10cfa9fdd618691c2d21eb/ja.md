```
cosine_similarity(u::AbstractVector, v::AbstractVector) -> Float
```

2つのベクトルのコサイン類似度を計算します。

# 例

```jldoctest
julia> cosine_similarity([1, 0], [1, 0])
1.0

julia> round(cosine_similarity([1,1], [1,0]), digits=3)
0.707

julia> cosine_similarity([1, 0], [0, 1])
0.0

julia> cosine_similarity([-1, 0], [1, 0])
-1.0

julia> round(cosine_similarity([1,0,0], [1,1,1]), digits=3)
0.577
```
