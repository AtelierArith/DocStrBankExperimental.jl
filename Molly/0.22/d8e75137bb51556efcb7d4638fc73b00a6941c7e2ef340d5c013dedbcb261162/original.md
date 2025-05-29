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

Calculate the force between atoms due to a given interaction type.

For pairwise interactions returns a single force vector and for specific interactions returns a type such as [`SpecificForce2Atoms`](@ref). Custom pairwise and specific interaction types should implement this function.
