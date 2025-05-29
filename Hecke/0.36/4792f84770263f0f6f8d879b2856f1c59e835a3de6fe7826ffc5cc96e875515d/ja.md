```
is_primitive(M::ZZLat, N::ZZLat) -> Bool
```

2つの$\mathbb Z$-ラティス$N \subseteq M$が与えられたとき、`N`が`M`の原始部分ラティスであるかどうかを返します。

# 例

```jldoctest
julia> U = hyperbolic_plane_lattice(3);

julia> bU = basis_matrix(U);

julia> e1, e2 = bU[1:1,:], bU[2:2,:]
([1 0], [0 1])

julia> N = lattice_in_same_ambient_space(U, e1 + e2)
整数ラティスの階数1および次数2
グラム行列
[6]

julia> is_primitive(U, N)
true

julia> M = root_lattice(:A, 3);

julia> f = matrix(QQ, 3, 3, [0 1 1; -1 -1 -1; 1 1 0]);

julia> N = kernel_lattice(M, f+1)
整数ラティスの階数1および次数3
グラム行列
[4]

julia> is_primitive(M, N)
true
```
