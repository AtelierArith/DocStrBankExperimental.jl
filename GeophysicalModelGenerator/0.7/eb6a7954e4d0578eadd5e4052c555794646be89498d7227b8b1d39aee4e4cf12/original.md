```
compute_thermal_structure(Temp, X, Y, Z, Phase, s::McKenzie_subducting_slab)
```

Compute the temperature field of a `McKenzie_subducting_slab`. Uses the analytical solution of McKenzie (1969) ["Speculations on the consequences and causes of plate motions"]. The functions assumes that the bottom of the slab is the coordinate Z=0. Internally the function shifts the coordinate.

Parameters

=============================

  * `Temp`:  Temperature array
  * `X`:    X Array
  * `Y`:    Y Array
  * `Z`:    Z Array
  * `Phase`: Phase array
  * `s`:    `McKenzie_subducting_slab`
