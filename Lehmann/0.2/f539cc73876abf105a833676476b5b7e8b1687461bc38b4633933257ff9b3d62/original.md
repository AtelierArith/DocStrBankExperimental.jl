```
struct DLRGrid
```

DLR grids for imaginary-time/Matsubara frequency correlators

#Members:

  * `isFermi`: bool is fermionic or bosonic
  * `symmetry`: particle-hole symmetric :ph, or particle-hole asymmetric :pha, or :none
  * `Euv` : the UV energy scale of the spectral density
  * `β` or `beta` : inverse temeprature
  * `Λ` or `lambda`: cutoff = UV Energy scale of the spectral density * inverse temperature
  * `rtol`: tolerance absolute error
  * `size` : number of DLR basis
  * `ω` or `omega` : selected representative real-frequency grid
  * `n` : selected representative Matsubara-frequency grid (integer)
  * `ωn` or `omegaN` : (2n+1)π/β
  * `τ` or `tau` : selected representative imaginary-time grid
