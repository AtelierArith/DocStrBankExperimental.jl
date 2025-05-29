```
function calc_bands(tbc::tb_crys, kpoints::Array{Float64,2}; spin=1)
```

Calculate bandstructure for k-points from k-point array. Returns eigenvalues.

# Arguments

  * `tbc::tb_crys` - The tight binding object
  * `kpoints::Array{Float64,2}` - k-point array. e.g. `[0.0 0.0 0.0; 0.0 0.0 0.1]`
  * `spin::Int` - spin component (1 or 2) if magnetic, only 1 is non-sp.
