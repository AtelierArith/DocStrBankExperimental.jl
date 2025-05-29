```
etm_amplitudes(ψin,m,grd,λ)
etm_amplitudes(ψin,m,grd,λ,em,sup,sub)
```

Computes the amplitude vectors of forward and backward propagating waves throught the ETM method

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

  * `a` : amplitude vectors of forward waves
  * `b` : amplitude vectors of backward waves
