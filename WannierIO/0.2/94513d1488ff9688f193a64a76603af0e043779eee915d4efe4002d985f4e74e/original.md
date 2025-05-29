```
write_nnkp(filename; toml=false, kwargs...)
write_nnkp(filename, ::Wannier90Text; kwargs...)
write_nnkp(filename, ::Wannier90Toml; kwargs...)
```

Write a `nnkp` file that can be used by DFT codes, e.g., QE `pw2wannier90`.

# Keyword Arguments

  * `toml`: write to a TOML file, otherwise write to a Wannier90 text file format
  * `recip_lattice`: each column is a reciprocal lattice vector
  * `kpoints`: length-`n_kpts` vector of `Vec3`, in fractional coordinates
  * `kpb_k`: length-`n_kpts` vector, each element is a length-`n_bvecs` vector of   integers, index of kpoints
  * `kpb_G`: length-`n_kpts` vector, each element is a length-`n_bvecs` vector,   then each element is a `Vec3` for translation vector, fractional w.r.t. `recip_lattice`
  * `projections`: optional, length-`n_projs` vector of `HydrogenOrbital`
  * `auto_projections`: optional, the number of Wannier functions `n_wann` for automatic   initial projections. If given, write an `auto_projections` block
  * `exclude_bands`: if given, write the specified band indices in the `exclude_bands` block
  * `header`: first line of the file
