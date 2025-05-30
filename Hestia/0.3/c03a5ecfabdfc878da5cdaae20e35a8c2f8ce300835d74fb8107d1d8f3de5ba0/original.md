```
DynamicAnisotropic <: AbstractAnisotropicProperty
```

Type DynamicAnisotropic contains the coefficients for anisotropic and temperature-dependent (dynamic) heat conduction

$$
    \lambda(\theta) = diag(\lambda_{x}(\theta),\lambda_{y}(\theta),\lambda_{z}(\theta))
$$

### Elements

`λx` : x-axis: thermal conductivity coefficients 

`λy` : y-axis: thermal conductivity coefficients

`λz` : z-axis: thermal conductivity coefficients

`ρ` : Mass density coefficients

`c` : Specific heat capacity coefficients
