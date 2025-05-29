```
generate_dos(bands::BandsWithSpin, kpoints::Array{KPoint, 1};
    smear::Function=gaussian, energy_number::Integer=10000)
```

Generate electronic density of states using bands and kpoints.

# Arguments

  * `bands::BandsWithSpin`: metadata of bands
  * `kpoints::Array{KPoint, 1}`: metadata of k-points
  * `smear::Function=gaussian`: smearing function, default: Gaussian smear
  * `energy_number::Integer=10000`: number of energy points, default 10000

# Returns

  * `dos1::DOS`: metadata of dos of spin up
  * `dos2::DOS`: metadata of dos of spin down
