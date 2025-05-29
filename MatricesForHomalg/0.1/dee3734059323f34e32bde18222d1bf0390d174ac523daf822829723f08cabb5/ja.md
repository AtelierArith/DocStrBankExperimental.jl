```
HomalgColumnVector(L, r, R)
```

リング R 上のリスト L のエントリを持つ (r x 1)-行列を構築します。

```jldoctest
julia> mat = HomalgColumnVector(1:5, 5, ZZ)
[1]
[2]
[3]
[4]
[5]
```
