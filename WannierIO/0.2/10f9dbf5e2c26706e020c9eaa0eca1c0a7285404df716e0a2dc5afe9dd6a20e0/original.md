```julia
write_w90_band_dat(filename; x, eigenvalues, extras)

```

Write `prefix_band.dat` file.

# Arguments

  * `filename`: filename of `prefix_band.dat`

# Keyword Arguments

  * `x`: `n_kpts`, x axis value, in cartesian length
  * `eigenvalues`: length-`n_kpts` vector, each element is a length-`n_bands`   vector of band energies
  * `extras`: optional, same size as `eigenvalues`, will be written as the third   column of `prefix_band.dat`. The `prefix-band.dat` file generated by   `postw90.x` sometimes has a third column for e.g. the color of the eigenvalues
