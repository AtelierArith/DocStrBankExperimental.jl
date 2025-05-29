```
potential_energy(system, neighbors=find_neighbors(sys), step_n=0; n_threads=Threads.nthreads())
```

Calculate the potential energy of a system using the pairwise, specific and general interactions.

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

Calculate the potential energy due to a given interaction type.

Custom interaction types should implement this function.
