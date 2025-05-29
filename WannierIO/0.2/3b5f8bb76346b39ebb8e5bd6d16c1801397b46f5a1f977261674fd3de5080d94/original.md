```julia
write_w90_band_labelinfo(
    filename;
    x,
    kpoints,
    symm_point_indices,
    symm_point_labels
)

```

Write `prefix_band.labelinfo` file.

# Arguments

  * `filename`: filename of `prefix_band.labelinfo`

# Keyword Arguments

  * `x`: `n_kpts`-vector, x axis value, in cartesian length
  * `kpoints`: length-`n_kpts` vector, fractional coordinates
  * `symm_point_indices`: index of high-symmetry points in `prefix_band.dat`
  * `symm_point_labels`: name of high-symmetry points
