```
MolecularForceField(ff_files...; units=true)
MolecularForceField(T, ff_files...; units=true)
MolecularForceField(atom_types, residue_types, bond_types, angle_types,
                    torsion_types, torsion_order, weight_14_coulomb,
                    weight_14_lj, attributes_from_residue)
```

A molecular force field.

Read one or more OpenMM force field XML files by passing them to the constructor.
