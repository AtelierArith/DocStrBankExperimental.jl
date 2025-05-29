```julia
write_xsf(filename, lattice, atom_positions, atom_numbers)
write_xsf(
    filename,
    lattice,
    atom_positions,
    atom_numbers,
    origin
)
write_xsf(
    filename,
    lattice,
    atom_positions,
    atom_numbers,
    origin,
    span_vectors
)
write_xsf(
    filename,
    lattice,
    atom_positions,
    atom_numbers,
    origin,
    span_vectors,
    W
)

```

Write `xsf` file.

# Arguments

  * `lattice`: `3 * 3`, Å, each column is a lattice vector
  * `atom_positions`: length-`n_atoms` vector, fractional coordinates
  * `atom_numbers`: `n_atoms`, atomic numbers
  * `origin`: `3`, Å, origin of the grid
  * `span_vectors`: `3 * 3`, Å, each column is a spanning vector
  * `W`: `nx * ny * nz`, volumetric data
