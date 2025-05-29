```
write_mmn(filename; M, kpb_k, kpb_G; header=default_header(), binary=false)
write_mmn(filename; M, kpb_k, kpb_G, ::FortranText; header=default_header(), binary=false)
write_mmn(filename; M, kpb_k, kpb_G, ::FortranBinaryStream; header=default_header(), binary=false)
```

Write wannier90 `mmn` file.

# Arguments

  * `filename`: output file name
  * `M`: length-`n_kpts` vector of `n_bands * n_bands * n_bvecs` arrays
  * `kpb_k`: length-`n_kpts` vector of length-`n_bvecs` vector of integers
  * `kpb_G`: length-`n_kpts` vector of length-`n_bvecs` vector of `Vec3{Int}` for bvectors

# Keyword arguments

  * `header`: header string
  * `binary`: if true write in Fortran binary format

The 1st version is a convenience wrapper for the other two.
