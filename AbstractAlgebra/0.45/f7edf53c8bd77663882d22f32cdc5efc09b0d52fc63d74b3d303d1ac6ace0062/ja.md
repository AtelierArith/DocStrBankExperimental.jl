```
minors_iterator_with_position(A::MatElem, k::Int)
```

行列 `A` の `k`-小行列を計算し、小行列の行と列のインデックスも指定するイテレータを返します。

# 例

```jldoctest
julia> A = ZZ[1 2 3; 4 5 6]
[1   2   3]
[4   5   6]

julia> first(minors_iterator_with_position(A, 2))
(-3, [1, 2], [1, 2])

```
