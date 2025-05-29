```
root_sublattice(L::ZZLat) -> ZZLat
```

長さが最大$2$の根によって張られたサブラティスを返します。

入力:

`L` - 定義された整数ラティス

出力:

$$
|x^2|\leq 2
$$

を満たすすべてのベクトル`x`によって`L`が張るサブラティス。

# 例

```jldoctest
julia> L = integer_lattice(gram = ZZ[2 0; 0 4]);

julia> root_sublattice(L)
Integer lattice of rank 1 and degree 2
with gram matrix
[2]

julia> basis_matrix(root_sublattice(L))
[1   0]
```
