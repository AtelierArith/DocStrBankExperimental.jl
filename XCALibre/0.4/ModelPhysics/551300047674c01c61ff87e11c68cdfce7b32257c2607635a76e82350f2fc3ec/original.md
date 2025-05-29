```
energy::SensibleEnthalpyModel, model::Physics{T1,F,M,Tu,E,D,BI}, prev, mdotf, rho, mueff, time, config
) where {T1,F,M,Tu,E,D,BI,E1}
```

Run energy transport equations.

### Input

  * `energy` – Energy model.
  * `model`  – Physics model defined by user.
  * `prev`   – Previous energy cell values.
  * `mdtof`  – Face mass flow.
  * `rho`    – Density ScalarField.
  * `mueff`  – Effective viscosity FaceScalarField.
  * `time`   –
  * `config` – Configuration structure defined by user with solvers, schemes, runtime and              hardware structures set.
