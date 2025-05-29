```
append(p::Permutation, ::Val{M})
```

与えられた置換に `M` の非置換次元を追加します。

# 例

```jldoctest
julia> append(Permutation(2, 3, 1), Val(2))
Permutation(2, 3, 1, 4, 5)

julia> append(NoPermutation(), Val(2))
NoPermutation()
```
