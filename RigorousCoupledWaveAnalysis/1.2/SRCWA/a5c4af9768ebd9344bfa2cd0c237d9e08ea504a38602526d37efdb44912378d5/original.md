```
srcwa_amplitudes(ψin,m,grd,λ)
srcwa_amplitudes(ψin,grd,mtr)
```

Computes the propagating wave amplituded vectors between layer interfaces according to the S-matrix method

# Arguments

  * `ψin` :  incoming (source) amplitude vector
  * `m` :  RCWA model object
  * `grd` : RCWA grid object
  * `λ` : free-space wavelength
  * `mtr` :  array with scattering matrices includeing superstrate and substrate

lation)  

# Outputs

  * `a` : array of forward propagating wave amplitudes
  * `b` : array of backward propagating wave amplitudes
