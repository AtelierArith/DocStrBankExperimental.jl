```
interpretations(valuations, p)
interpretations(p)
```

各[`valuations`](@ref)で`p`を[`interpret`](@ref)した結果として与えられる`Array{Bool}`を返します。

# 例

```jldoctest
julia> collect(interpretations(⊤))
0次元 Array{Bool, 0}:
1

julia> @atomize collect(interpretations(p))
2要素のベクトル{Bool}:
 1
 0

julia> @atomize collect(interpretations(p ∧ q))
2×2 行列{Bool}:
 1  0
 0  0
```
