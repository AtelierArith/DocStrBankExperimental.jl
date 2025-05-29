```
prepend(p::Permutation, ::Val{M})
```

与えられた置換に `M` の非置換次元を追加します。

# 例

```jldoctest
julia> prepend(Permutation(2, 3, 1), Val(2))
Permutation(1, 2, 4, 5, 3)

julia> prepend(NoPermutation(), Val(2))
NoPermutation()
```
