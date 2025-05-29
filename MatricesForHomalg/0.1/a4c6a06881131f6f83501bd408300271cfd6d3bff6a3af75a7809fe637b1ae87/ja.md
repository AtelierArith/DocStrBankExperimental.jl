```
HomalgColumnVector(L, r, R)
```

リスト L の要素を持つ、環 R 上の (r x 1) 行列を構築します。ここで、r = length(L)

```jldoctest
julia> mat = HomalgColumnVector(1:5, ZZ)
[1]
[2]
[3]
[4]
[5]
```
