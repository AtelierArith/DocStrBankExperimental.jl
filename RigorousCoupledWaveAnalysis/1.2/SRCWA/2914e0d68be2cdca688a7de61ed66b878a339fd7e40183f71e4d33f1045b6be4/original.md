```
srcwa_reftra(ψin,m,grd,λ)
srcwa_reftra(ψin,εsup,εsub,S,grd,λ)
```

Computes reflection and transmission according to the S-matrix method

# Arguments

  * `ψin` :  incoming (source) amplitude vector
  * `m` :  RCWA model object
  * `grd` : RCWA grid object
  * `λ` : free-space wavelength
  * `S` :  total scattering matrix of the device (computed from m if not given)
  * `εsup` :  superstrate material object (taken from m if not given)
  * `εsub` :  substrate material object (taken from m if not given)

lation)

# Outputs

  * `R` : reflection by the device
  * `T` : transmission by the device
