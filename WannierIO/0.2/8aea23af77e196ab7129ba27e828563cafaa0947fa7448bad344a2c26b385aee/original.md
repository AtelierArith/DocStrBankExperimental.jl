```julia
write_w90_band_kpt(filename; kpoints, kweights)

```

Write `prefix_band.kpt` file.

# Arguments

  * `filename`: filename of `prefix_band.kpt`

# Keyword Arguments

  * `kpoints`: length-`n_kpts` vector, fractional coordinates
  * `kweights`: `n_kpts`, optional, weights of kpoints, default to 1.0.
