```
mutable struct dftout
```

DFT output struct. Has

  * `crys::crystal`  crystal structure
  * `energy::Float64` the actual DFT energy, depends on pseudopotentials.
  * `energy_smear::Float64` smearing energy
  * `forces::Array{Float64,2}` forces Ryd / a.u.
  * `stress::Array{Float64,2}` stress  Ryd / (a.u.)^3
  * `bandstruct::bandstructure` See bandstructure struct
  * `hasband::Bool` does this object have a band structure, usually `true`
  * `hasham::Bool` not used, always `false`
  * `prefix::String`  A string has a name used to find output files.
  * `outdir::String` Directly loaded from
  * `tot_charge::Float64` If charge of unit cell is nonzero
  * `atomize_energy::Float64` Atomization energy, relative to non-spin-polarized atoms.
  * `nspin::Int64` number of spins (1 = non-sp, 2= spin-polarized)
  * `mag_tot::Float64` Total magnetization  = sum*i mag*i
  * `mag_abs::Float64` Absolute magnetization = sum*i | mag*i |
