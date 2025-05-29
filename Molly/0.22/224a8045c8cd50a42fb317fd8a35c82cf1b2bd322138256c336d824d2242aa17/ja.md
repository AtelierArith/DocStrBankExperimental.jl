```
MolecularForceField(ff_files...; units=true)
MolecularForceField(T, ff_files...; units=true)
MolecularForceField(atom_types, residue_types, bond_types, angle_types,
                    torsion_types, torsion_order, weight_14_coulomb,
                    weight_14_lj, attributes_from_residue)
```

分子力場。

コンストラクタに渡すことで、1つ以上のOpenMM力場XMLファイルを読み込みます。
