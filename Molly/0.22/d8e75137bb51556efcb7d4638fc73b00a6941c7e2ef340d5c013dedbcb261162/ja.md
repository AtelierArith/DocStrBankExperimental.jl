```
force(inter, vec_ij, atom_i, atom_j, force_units, special, coord_i, coord_j,
      boundary, velocity_i, velocity_j, step_n)
force(inter, coord_i, boundary, atom_i, force_units, velocity_i, step_n)
force(inter, coord_i, coord_j, boundary, atom_i, atom_j, force_units, velocity_i,
      velocity_j, step_n)
force(inter, coord_i, coord_j, coord_k, boundary, atom_i, atom_j, atom_k,
      force_units, velocity_i, velocity_j, velocity_k, step_n)
force(inter, coord_i, coord_j, coord_k, coord_l, boundary, atom_i, atom_j, atom_k,
      atom_l, force_units, velocity_i, velocity_j, velocity_k, velocity_l, step_n)
```

与えられた相互作用タイプによる原子間の力を計算します。

ペアワイズ相互作用の場合は単一の力ベクトルを返し、特定の相互作用の場合は[`SpecificForce2Atoms`](@ref)のようなタイプを返します。カスタムペアワイズおよび特定の相互作用タイプは、この関数を実装する必要があります。
