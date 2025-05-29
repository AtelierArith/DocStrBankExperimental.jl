```
HomalgDiagonalMatrix(L, R)
```

リング R 上で対角成分のリスト L を使用して対角行列を構築します。

```jldoctest
julia> mat = HomalgDiagonalMatrix(1:5, ZZ)
[1   0   0   0   0]
[0   2   0   0   0]
[0   0   3   0   0]
[0   0   0   4   0]
[0   0   0   0   5]
```
