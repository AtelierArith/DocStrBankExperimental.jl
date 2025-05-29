Problem state for ChabocheThermal material.

  * `stress`: stress tensor
  * `R`: yield strength (isotropic hardening)
  * `X1`: backstress 1 (kinematic hardening)
  * `X2`: backstress 2 (kinematic hardening)
  * `X3`: backstress 3 (kinematic hardening)
  * `plastic_strain`: plastic part of strain tensor
  * `cumeq`: cumulative equivalent plastic strain (scalar, ≥ 0)
  * `jacobian`: ∂σij/∂εkl (algorithmic)

The other `dXXXdYYY` properties are the algorithmic jacobians for the indicated variables.

The elastic and thermal contributions to the strain tensor are not stored. To get them:

```
θ₀ = ...
θ = ...
p = material.parameters
v = material.variables

C(θ) = compliance_tensor(p.E, p.nu, θ)
elastic_strain = dcontract(C(θ), v.stress)

thermal_strain = thermal_strain_tensor(p.alpha, θ₀, θ)
```

Then it holds that:

```
material.drivers.strain = elastic_strain + v.plastic_strain + thermal_strain
```
