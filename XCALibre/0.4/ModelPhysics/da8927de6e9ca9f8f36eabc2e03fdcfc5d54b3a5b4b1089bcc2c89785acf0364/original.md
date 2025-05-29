```
function initialise(
    turbulence::Laminar, model::Physics{T,F,M,Tu,E,D,BI}, mdotf, peqn, config
    ) where {T,F,M,Tu,E,D,BI}
return LaminarModel()
```

end

Initialisation of turbulent transport equations.

### Input

  * `turbulence` – turbulence model.
  * `model`  – Physics model defined by user.
  * `mdtof`  – Face mass flow.
  * `peqn`   – Pressure equation.
  * `config` – Configuration structure defined by user with solvers, schemes, runtime and          hardware structures set.

### Output

  * `LaminarModel()`  – Turbulence model structure.
