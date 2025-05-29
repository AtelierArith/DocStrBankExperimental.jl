```julia
write_w90_band(
    prefix;
    x,
    eigenvalues,
    kpoints,
    kweights,
    symm_point_indices,
    symm_point_labels
)

```

Write `prefix_band.dat, prefix_band.kpt, prefix_band.labelinfo.dat`.

# Arguments

  * `prefix`: prefix of `prefix_band.dat, prefix_band.kpt, prefix_band.labelinfo.dat`

# Keyword Arguments

  * `x`: `n_kpts`, x axis value, in cartesian length
  * `eigenvalues`: length-`n_kpts` vector, each element is a length-`n_bands` vector of band energies
  * `kpoints`: length-`n_kpts` vector, fractional coordinates
  * `kweights`: a vector of length `n_kpts`, weights of kpoints
  * `symm_point_indices`: index of high-symmetry points in `prefix_band.dat`
  * `symm_point_labels`: name of high-symmetry points
