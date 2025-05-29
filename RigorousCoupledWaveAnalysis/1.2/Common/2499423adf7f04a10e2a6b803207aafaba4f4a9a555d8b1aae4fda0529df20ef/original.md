```
get_permittivity(mat::Material,λ)
get_permittivity(mat::Material,λ,index)
```

Returns the permittivity of a material model object for given wavelength and coordinate direction

# Arguments

  * `mat` :  material object
  * `λ` :  free space wavelength
  * `index` :  optional, specifies the coordinate direction for anisotropic materials

# Outputs

  * `ε` : Complex scalar permittivity value for the given wavelength and coordinate direction
