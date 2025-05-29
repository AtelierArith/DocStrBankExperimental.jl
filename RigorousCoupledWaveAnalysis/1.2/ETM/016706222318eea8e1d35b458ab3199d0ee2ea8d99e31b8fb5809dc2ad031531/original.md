```
etm_propagate(sup,sub,em,ψin,grd)
etm_propagate(sup,sub,em,ψin,grd,get_r)
```

The propagation of waves according to the ETM method

# Arguments

  * `sup` :  superstrate halfspace object
  * `sub` :  substrate halfspace object
  * `em` :  array with eigenmodes for all layers
  * `ψin` :  incoming (source) amplitude vector
  * `grd` : RCWA grid object
  * `get_r` : set false if you do not need the internal backward propagating waves (only required for absorption calculation)

# Outputs

  * `ψref` : reflected amplitude vector
  * `ψtra` : transmitted amplitude vector
  * `ψp` : array of internal back propagating wave vectors in each layer
  * `ψm` : array of internal forward propagating wave vectors in each layer
