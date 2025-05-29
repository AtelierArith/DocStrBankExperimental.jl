```
HomalgRowVector(L, c, R)
```

リング R 上のリスト L のエントリを持つ (1 x c)-行列を構築します。

```jldoctest
julia> mat = HomalgRowVector(1:5, 5, ZZ)
[1   2   3   4   5]
```
