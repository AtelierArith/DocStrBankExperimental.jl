```julia
write_cube(
    filename,
    atom_positions,
    atom_numbers,
    origin,
    voxel_vectors,
    W
)

```

Write `cube` file.

# Arguments

  * `atom_positions`: `3 * n_atoms`, Å, cartesian coordinates
  * `atom_numbers`: `n_atoms`, atomic numbers
  * `origin`: `3`, Å, origin of the grid
  * `voxel_vectors`: `3 * 3`, Å, each column is a voxel vector
  * `W`: `nx * ny * nz`, volumetric data
