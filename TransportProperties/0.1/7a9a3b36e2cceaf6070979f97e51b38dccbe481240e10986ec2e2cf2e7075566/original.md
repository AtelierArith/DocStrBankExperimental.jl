Function for calculating diffusion coefficient of a species in a mixture

# Usage

```
D_km!(Dkm, sp_trd, T, p, molwt, molefracs)
```

  * Dkm : Array for storing the mixture diffusion coefficients
  * sp_trd : Array of the type TransportData
  * T : temperature in K
  * p : Pressure in Pa
  * molwt : species molecular weights
  * molefracs : species mole fractions
