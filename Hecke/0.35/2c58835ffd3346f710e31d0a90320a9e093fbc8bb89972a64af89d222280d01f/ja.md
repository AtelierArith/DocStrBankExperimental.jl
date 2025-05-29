```
primitive_closure(M::ZZLat, N::ZZLat) -> ZZLat
```

2つの$\mathbb Z$-格子`M`と`N`が$N \subseteq \mathbb{Q} M$であるとき、`M`における`N`の原始閉包$M \cap \mathbb{Q} N$を返します。

# 例

```jldoctest
julia> M = root_lattice(:D, 6);

julia> N = lattice_in_same_ambient_space(M, 3*basis_matrix(M)[1:1,:]);

julia> basis_matrix(N)
[3   0   0   0   0   0]

julia> N2 = primitive_closure(M, N)
整数格子の階数 1 と次数 6
グラム行列
[2]

julia> basis_matrix(N2)
[1   0   0   0   0   0]

julia> M2 = primitive_closure(dual(M), M);

julia> is_integral(M2)
false

```
