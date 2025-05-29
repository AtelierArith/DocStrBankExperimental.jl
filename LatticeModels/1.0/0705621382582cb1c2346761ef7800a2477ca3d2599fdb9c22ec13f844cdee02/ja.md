```
AdjacencyMatrix{LT} where {LT<:Lattice}
```

いくつかの格子上の結合を表します。

---

```
AdjacencyMatrix(lat[, mat])
```

`lat` 格子上の `mat` 行列から隣接行列を構築します。

`mat` が提供されていない場合、ゼロ行列であると見なされます。

## 例

```jldoctest
julia> using LatticeModels

julia> l = SquareLattice(2, 2);

julia> a = AdjacencyMatrix(l)
2D空間の4サイトのSquareLattice上の隣接行列
0が格納されたエントリを持つ4×4 SparseArrays.SparseMatrixCSC{Bool, Int64}の値:
 ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅

julia> site1, site2, site3, site4 = l;

julia> a[site1, site2] = a[site2, site4] = a[site3, site4] = true;

julia> a
2D空間の4サイトのSquareLattice上の隣接行列
6が格納されたエントリを持つ4×4 SparseArrays.SparseMatrixCSC{Bool, Int64}の値:
 ⋅  1  ⋅  ⋅
 1  ⋅  ⋅  1
 ⋅  ⋅  ⋅  1
 ⋅  1  1  ⋅
```
