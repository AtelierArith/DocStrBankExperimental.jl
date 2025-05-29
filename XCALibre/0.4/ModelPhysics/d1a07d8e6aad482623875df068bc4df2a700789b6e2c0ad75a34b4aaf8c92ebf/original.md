```
initialise(energy::SensibleEnthalpy, model::Physics{T1,F,M,Tu,E,D,BI}, mdotf, rho, peqn, config
) where {T1,F,M,Tu,E,D,BI})
```

Initialisation of energy transport equations.

### Input

  * `energy` – Energy model.
  * `model`  – Physics model defined by user.
  * `mdtof`  – Face mass flow.
  * `rho`    – Density ScalarField.
  * `peqn`   – Pressure equation.
  * `config` – Configuration structure defined by user with solvers, schemes, runtime and              hardware structures set.

### Output

  * `SensibleEnthalpyModel`  – Energy model struct containing energy equation.
