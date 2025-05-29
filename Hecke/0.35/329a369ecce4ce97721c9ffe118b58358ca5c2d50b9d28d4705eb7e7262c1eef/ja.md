```
gram_matrix(L::ZZLat) -> QQMatrix
```

$$
L
$$

のグラム行列を返します。

# 例

```jldoctest
julia> L = integer_lattice(matrix(ZZ, [2 0; -1 2]));

julia> gram_matrix(L)
[ 4   -2]
[-2    5]
```
