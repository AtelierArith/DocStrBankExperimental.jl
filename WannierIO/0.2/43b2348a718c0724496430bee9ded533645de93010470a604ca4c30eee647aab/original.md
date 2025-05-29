```julia
write_bxsf(filename, fermi_energy, origin, span_vectors, E)

```

Write `bxsf` file.

# Arguments

  * `fermi_energy`: Fermi energy in eV
  * `origin`: `3`, Å⁻¹, origin of the grid
  * `span_vectors`: `3 * 3`, Å⁻¹, each column is a spanning vector
  * `E`: `n_bands * nx * ny * nz`, eigenvalues at each grid point
