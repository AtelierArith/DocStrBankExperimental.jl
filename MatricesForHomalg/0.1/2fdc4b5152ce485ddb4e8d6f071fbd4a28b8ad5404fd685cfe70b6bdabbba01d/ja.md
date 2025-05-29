```
HomalgRowVector(L, R)
```

リング R 上にリスト L のエントリを持つ (1 x c)-行列を構築します。ここで、c = length(L) です。

```jldoctest
julia> mat = HomalgRowVector(1:5, ZZ)
[1   2   3   4   5]
```
