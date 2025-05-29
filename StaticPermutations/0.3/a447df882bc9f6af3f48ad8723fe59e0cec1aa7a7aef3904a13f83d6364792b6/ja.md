```
isidentity(p::Permutation)
```

`p` が恒等置換である場合、すなわち `(1, 2, 3, ...)` と同等である場合に `true` を返します。

```jldoctest
julia> isidentity(Permutation(1, 2, 3))
true

julia> isidentity(Permutation(1, 3, 2))
false

julia> isidentity(NoPermutation())
true
```
