```
initialise(turbulence::KOmegaLKE, model::Physics{T,F,M,Tu,E,D,BI}, mdotf, peqn, config
) where {T,F,M,Tu,E,D,BI}
```

Initialisation of turbulent transport equations.

### Input

  * `turbulence` – turbulence model.
  * `model`  – Physics model defined by user.
  * `mdtof`  – Face mass flow.
  * `peqn`   – Pressure equation.
  * `config` – Configuration structure defined by user with solvers, schemes, runtime and          hardware structures set.

### Output

  * `KOmegaLKEModel(       turbulence,       k_eqn,       ω_eqn,       kl_eqn,       nueffkLS,       nueffkS,       nueffωS,       nuL,       nuts,       Ω,       γ,       fv,       normU,       Reυ,       ∇k,       ∇ω,        state   )`  – Turbulence model structure.
