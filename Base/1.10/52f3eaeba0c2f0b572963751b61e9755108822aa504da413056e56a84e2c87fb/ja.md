```
allequal(itr) -> Bool
```

`itr`のすべての値が[`isequal`](@ref)で比較したときに等しい場合は`true`を返します。

関連: [`unique`](@ref), [`allunique`](@ref).

!!! compat "Julia 1.8"
    `allequal`関数は少なくともJulia 1.8が必要です。


# 例

```jldoctest
julia> allequal([])
true

julia> allequal([1])
true

julia> allequal([1, 1])
true

julia> allequal([1, 2])
false

julia> allequal(Dict(:a => 1, :b => 1))
false
```
