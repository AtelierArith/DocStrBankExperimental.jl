```
potential_energy(system, neighbors=find_neighbors(sys), step_n=0; n_threads=Threads.nthreads())
```

システムのポテンシャルエネルギーをペアワイズ、特定および一般的な相互作用を使用して計算します。

```
potential_energy(inter, vec_ij, atom_i, atom_j, energy_units, special, coord_i, coord_j,
                 boundary, velocity_i, velocity_j, step_n)
potential_energy(inter, coord_i, boundary, atom_i, energy_units, velocity_i, step_n)
potential_energy(inter, coord_i, coord_j, boundary, atom_i, atom_j, energy_units,
                 velocity_i, velocity_j, step_n)
potential_energy(inter, coord_i, coord_j, coord_k, boundary, atom_i, atom_j, atom_k,
                 energy_units, velocity_i, velocity_j, velocity_k, step_n)
potential_energy(inter, coord_i, coord_j, coord_k, coord_l, boundary, atom_i, atom_j,
                 atom_k, atom_l, energy_units, velocity_i, velocity_j, velocity_k,
                 velocity_l, step_n)
```

特定の相互作用タイプによるポテンシャルエネルギーを計算します。

カスタム相互作用タイプはこの関数を実装する必要があります。
