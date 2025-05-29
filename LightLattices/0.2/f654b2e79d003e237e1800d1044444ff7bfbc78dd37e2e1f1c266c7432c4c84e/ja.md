```julia
relative_coordinate(
    lattice::LightLattices.RegularLattice{D, T, true, <:LightLattices.TrivialCell},
    I1::CartesianIndex{D},
    I2::CartesianIndex{D}
) -> Any

```

周期的格子の場合、「最短」相対座標が計算されます。

そのために、次のヒューリスティックが使用されます。2つのノードのカートesianインデックスは同じ量だけシフトされ、2番目のノードのカートesianインデックスが格子の中央セルに対応するようにします。次に、最初のノードのカートesianインデックスが格子内に戻されます。相対座標は、得られたインデックスを使用して計算されます。

このヒューリスティックは、`relative_coordinate(lattice, I1, I2) == -relative_coordinate(lattice, I2, I1)`を保証します。
