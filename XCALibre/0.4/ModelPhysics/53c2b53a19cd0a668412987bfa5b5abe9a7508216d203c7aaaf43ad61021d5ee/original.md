```
initialise(turbulence::KOmega, model::Physics{T,F,M,Tu,E,D,BI}, mdotf, peqn, config
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

  * `KOmegaModel(       turbulence,       k_eqn,        ω_eqn,       state       )`  – Turbulence model structure.
