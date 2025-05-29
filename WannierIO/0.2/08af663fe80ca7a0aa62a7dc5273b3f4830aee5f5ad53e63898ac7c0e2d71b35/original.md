```
read_nnkp(filename)
read_nnkp(filename, ::Wannier90Text)
read_nnkp(filename, ::Wannier90Toml)
```

Read wannier90 `nnkp` file.

# Return

  * `lattice`: each column is a lattice vector
  * `recip_lattice`: each column is a reciprocal lattice vector
  * `kpoints`: length-`n_kpts` vector, each element is `Vec3`, in fractional coordinates
  * `projections`: length-`n_projs` vector of `HydrogenOrbital`
  * `auto_projections`: optional, the number of Wannier functions `n_wann` for automatic   initial projections
  * `kpb_k`: length-`n_kpts` vector, each element is a length-`n_bvecs` vector of   integers, index of kpoints
  * `kpb_G`: length-`n_kpts` vector, each element is a length-`n_bvecs` vector,   then each element is `Vec3` for translations, fractional w.r.t `recip_lattice`

Wannier90 `nnkp` file is a plain text format, the 2nd version reads `nnkp` file in Wannier90 format. The thrid version read a TOML-format `nnkp` file, which is defined by this package, see [`write_nnkp`](@ref). The 1st version auto detects the format and parse it.
