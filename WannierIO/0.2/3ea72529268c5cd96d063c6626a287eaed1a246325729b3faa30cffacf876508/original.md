```julia
read_xsf(filename)

```

Read `xsf` file.

# Return

  * `primvec`: `3 * 3`, Å, each column is a primitive lattice vector
  * `convvec`: `3 * 3`, Å, each column is a conventional lattice vector
  * `atoms`: `n_atoms` String, atomic symbols or numbers
  * `atom_positions`: length-`n_atoms` vector, Å, cartesian coordinates
  * `origin`: `3`, Å, origin of the grid
  * `span_vectors`: `3 * 3`, Å, each column is a spanning vector
  * `X`: `nx`, fractional coordinate of grid points along the first spanning vector
  * `Y`: `ny`, fractional coordinate of grid points along the second spanning vector
  * `Z`: `nz`, fractional coordinate of grid points along the third spanning vector
  * `W`: `nx * ny * nz`, volumetric data

!!! note
    Only support reading 1 datagrid in `BLOCK_DATAGRID_3D`.

