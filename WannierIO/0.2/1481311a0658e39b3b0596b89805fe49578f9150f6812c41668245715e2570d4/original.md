```julia
read_bxsf(filename)

```

Read `bxsf` file.

# Return

  * `fermi_energy`: Fermi energy in eV
  * `origin`: `3`, Å⁻¹, origin of the grid
  * `span_vectors`: `3 * 3`, Å⁻¹, each column is a spanning vector
  * `X`: `nx`, fractional coordinate of grid points along the first spanning vector
  * `Y`: `ny`, fractional coordinate of grid points along the second spanning vector
  * `Z`: `nz`, fractional coordinate of grid points along the third spanning vector
  * `E`: `n_bands * nx * ny * nz`, eigenvalues at each grid point
