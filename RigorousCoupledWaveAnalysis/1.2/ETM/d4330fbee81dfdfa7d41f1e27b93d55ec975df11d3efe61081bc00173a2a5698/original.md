```
etm_reftra_flows(ψin,m,grd,λ)
etm_reftra_flows(ψin,m,grd,λ,em,sup,sub)
```

Computes reflection and transmission, as well as the net power flows between layers according to the ETM method

# Arguments

  * `ψin` :  incoming (source) amplitude vector
  * `m` :  RCWA model object
  * `grd` : RCWA grid object
  * `λ` : free-space wavelength
  * `em` :  array with eigenmodes for all layers (computed from m if not given)
  * `sup` :  superstrate halfspace object (computed from m if not given)
  * `sub` :  substrate halfspace object (computed from m if not given)

lation)

# Outputs

  * `R` : reflection by the device
  * `T` : transmission by the device
  * `flw` : array containing the power flows between layers
