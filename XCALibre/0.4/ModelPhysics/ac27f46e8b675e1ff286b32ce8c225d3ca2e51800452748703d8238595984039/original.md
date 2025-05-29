```
KOmegaLKE <: AbstractTurbulenceModel
```

kOmega model containing all kOmega field parameters.

### Fields

  * `k` – Turbulent kinetic energy ScalarField.
  * `omega` – Specific dissipation rate ScalarField.
  * `kl` – ScalarField.
  * `nut` – Eddy viscosity ScalarField.
  * `kf` – Turbulent kinetic energy FaceScalarField.
  * `omegaf` – Specific dissipation rate FaceScalarField.
  * `klf` – FaceScalarField.
  * `nutf` – Eddy viscosity FaceScalarField.
  * `coeffs` – Model coefficients.
  * `Tu` – Freestream turbulence intensity for model.
  * `y` – Near-wall distance for model.
