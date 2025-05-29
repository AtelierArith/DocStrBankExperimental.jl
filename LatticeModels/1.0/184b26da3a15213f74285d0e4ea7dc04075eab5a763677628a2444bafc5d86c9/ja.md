```
Currents(currents[, adjacency_matrix])
```

`currents`のための`Currents`インスタンスを作成します。

## 引数

  * `currents`: `Currents`に変換される`AbstractCurrents`オブジェクト。これは、すべてのペア間の電流の評価を必要とするため、時間がかかる場合があります。
  * `adjacency_matrix`: 提供される場合、電流は隣接するサイト間のみで評価されます。

## 例

```jldoctest
julia> using LatticeModels

julia> lat = SquareLattice(4, 4); site1, site2 = lat[1:2];

julia> H0 = tightbinding_hamiltonian(lat); psi = groundstate(H0);

julia> H1 = tightbinding_hamiltonian(lat, field=LandauGauge(0.1));

julia> currents = DensityCurrents(H1, psi)
Density currents for system:
One particle on 16-site SquareLattice in 2D space

julia> c2 = Currents(currents)
Currents{SparseArrays.SparseMatrixCSC{Float64, Int64}} on 16-site SquareLattice in 2D space

julia> c2[site1, site2] ≈ currents[site1, site2]
true
```
