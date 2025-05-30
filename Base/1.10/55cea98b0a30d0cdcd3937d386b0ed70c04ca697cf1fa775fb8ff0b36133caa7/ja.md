```
allunique(itr) -> Bool
```

`itr`のすべての値が[`isequal`](@ref)で比較したときに異なる場合は`true`を返します。

関連情報: [`unique`](@ref), [`issorted`](@ref), [`allequal`](@ref).

# 例

```jldoctest
julia> allunique([1, 2, 3])
true

julia> allunique([1, 2, 1, 2])
false

julia> allunique(Real[1, 1.0, 2])
false

julia> allunique([NaN, 2.0, NaN, 4.0])
false
```
