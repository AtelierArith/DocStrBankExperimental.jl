```
read_mmn(filename)
read_mmn(filename, ::FortranText)
read_mmn(filename, ::FortranBinaryStream)
```

Read wannier90 `mmn` file.

# Return

  * `M`: length-`n_kpts` vector, each element is a length-`n_bvecs` vector, then   each element is a `n_bands * n_bands` matrix
  * `kpb_k`: length-`n_kpts` vector, each element is a length-`n_bvecs` vector of   integers for the indices of the neighboring kpoints
  * `kpb_G`: length-`n_kpts` vector, each element is a lenght-`n_bvecs` vector of   of `Vec3{Int}`, which are the translation vectors
  * `header`: 1st line of the file

The translation vector `G` is defined as `b = kpoints[kpb_k[ik][ib]] + kpb_G[ik][ib] - kpoints[ik]`, where `b` is the `ib`-th bvector of the `ik`-th kpoint.

The 1st version is a convenience wrapper for the other two.
