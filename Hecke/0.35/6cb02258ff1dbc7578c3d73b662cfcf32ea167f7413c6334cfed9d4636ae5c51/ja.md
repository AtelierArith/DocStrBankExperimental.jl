```
integer_lattice([B::MatElem]; gram) -> ZZLat
```

基底行列 $B$ を持つ Z-格子を、グラム行列 `gram` を持つ二次空間内で返します。

キーワード `gram` が指定されていない場合、グラム行列は単位行列になります。$B$ が指定されていない場合、基底行列は単位行列になります。

# 例

```jldoctest
julia> L = integer_lattice(matrix(QQ, 2, 2, [1//2, 0, 0, 2]));

julia> gram_matrix(L) == matrix(QQ, 2, 2, [1//4, 0, 0, 4])
true

julia> L = integer_lattice(gram = matrix(ZZ, [2 -1; -1 2]));

julia> gram_matrix(L) == matrix(ZZ, [2 -1; -1 2])
true
```
