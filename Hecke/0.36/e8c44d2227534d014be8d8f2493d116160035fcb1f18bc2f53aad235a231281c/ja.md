```
leech_lattice(niemeier_lattice::ZZLat) -> ZZLat, QQMatrix, Int
```

三重項 `L, v, h` を返します。ここで `L` は Leech 格子です。

`L` は `v` に関して Niemeier 格子 `N` の `h`-隣接です。これは `L / L ∩ N  ≅ ℤ / h ℤ` を意味します。ここで `h` は Niemeier 格子のコクセター数です。

これは [CS99](@cite) における Leech 格子の 23 の神聖な構成を実装しています。

# 例

```jldoctest leech
julia> R = integer_lattice(gram=2 * identity_matrix(ZZ, 24));

julia> N = maximal_even_lattice(R) # 一部の Niemeier 格子
ランク 24 および次数 24 の整数格子
グラム行列
[2   1   1   1   0   0   0   0   0   0   0   0   0   0   0   0   1   0   1   1   0   0   0   0]
[1   2   1   1   0   0   0   0   0   0   0   0   0   0   0   0   1   1   0   1   0   0   0   0]
[1   1   2   1   0   0   0   0   0   0   0   0   0   0   0   0   1   1   1   0   0   0   0   0]
[1   1   1   2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0]
[0   0   0   0   2   1   1   1   0   0   0   0   1   0   1   1   0   0   0   0   0   0   0   0]
[0   0   0   0   1   2   1   1   0   0   0   0   1   1   0   1   0   0   0   0   0   0   0   0]
[0   0   0   0   1   1   2   1   0   0   0   0   1   1   1   0   0   0   0   0   0   0   0   0]
[0   0   0   0   1   1   1   2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0]
[0   0   0   0   0   0   0   0   2   1   1   1   0   0   0   0   0   0   0   0   1   1   1   0]
[0   0   0   0   0   0   0   0   1   2   1   1   0   0   0   0   0   0   0   0   1   0   1   1]
[0   0   0   0   0   0   0   0   1   1   2   1   0   0   0   0   0   0   0   0   1   1   0   1]
[0   0   0   0   0   0   0   0   1   1   1   2   0   0   0   0   0   0   0   0   0   0   0   0]
[0   0   0   0   1   1   1   0   0   0   0   0   2   1   1   1   0   0   0   0   0   0   0   0]
[0   0   0   0   0   1   1   0   0   0   0   0   1   2   0   0   0   0   0   0   0   0   0   0]
[0   0   0   0   1   0   1   0   0   0   0   0   1   0   2   0   0   0   0   0   0   0   0   0]
[0   0   0   0   1   1   0   0   0   0   0   0   1   0   0   2   0   0   0   0   0   0   0   0]
[1   1   1   0   0   0   0   0   0   0   0   0   0   0   0   0   2   1   1   1   0   0   0   0]
[0   1   1   0   0   0   0   0   0   0   0   0   0   0   0   0   1   2   0   0   0   0   0   0]
[1   0   1   0   0   0   0   0   0   0   0   0   0   0   0   0   1   0   2   0   0   0   0   0]
[1   1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   1   0   0   2   0   0   0   0]
[0   0   0   0   0   0   0   0   1   1   1   0   0   0   0   0   0   0   0   0   2   1   1   1]
[0   0   0   0   0   0   0   0   1   0   1   0   0   0   0   0   0   0   0   0   1   2   0   0]
[0   0   0   0   0   0   0   0   1   1   0   0   0   0   0   0   0   0   0   0   1   0   2   0]
[0   0   0   0   0   0   0   0   0   1   1   0   0   0   0   0   0   0   0   0   1   0   0   2]

julia> minimum(N)
2

julia> det(N)
1

julia> L, v, h = leech_lattice(N);

julia> minimum(L)
4

julia> det(L)
1

julia> h == index(L, intersect(L, N))
true

```

Leech 格子が `N`, `h` および `v` からどのように構成されるかを示します。

```jldoctest leech
julia> Zmodh, _ = residue_ring(ZZ, h);

julia> V = ambient_space(N);

julia> vG = map_entries(x->Zmodh(ZZ(x)), inner_product(V, v, basis_matrix(N)));

julia> LN = transpose(lift(Hecke.kernel(vG; side = :right)))*basis_matrix(N); # `v` との内積が `h` で割り切れるベクトル。

julia> M = lattice(V, LN) + h*N;

julia> M == intersect(L, N)
true

julia> M + lattice(V, 1//h * v) == L
true

```
