```
displacement_height(model::AbstractModel, Y, p)
```

A helper function which returns the displacement height  for a given model; the default is zero.

Extending this function for your model is only necessary if you need to compute surface fluxes and radiative fluxes at the surface using the functions in this file.
