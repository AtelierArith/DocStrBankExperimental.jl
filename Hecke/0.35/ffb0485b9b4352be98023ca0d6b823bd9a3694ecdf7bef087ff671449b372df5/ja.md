```
rational_span(L::ZZLat) -> QuadSpace
```

$$
L
$$

の有理スパンを返します。これは、`gram_matrix(L)`と等しいグラム行列を持つ二次空間です。

# 例

```jldoctest
julia> L = integer_lattice(matrix(ZZ, [2 0; -1 2]));

julia> rational_span(L)
Quadratic space of dimension 2
  over rational field
with gram matrix
[ 4   -2]
[-2    5]
```
