```
turbulence!(les::SmagorinskyModel, model::Physics{T,F,M,Tu,E,D,BI}, S, S2, prev, time, config
) where {T,F,M,Tu<:AbstractTurbulenceModel,E,D,BI}
```

Run turbulence model transport equations.

### Input

  * `les::SmagorinskyModel` – Smagorinsky LES turbulence model.
  * `model`  – Physics model defined by user.
  * `S`   – Strain rate tensor.
  * `S2`  – Square of the strain rate magnitude.
  * `prev`  – Previous field.
  * `time`   –
  * `config` – Configuration structure defined by user with solvers, schemes, runtime and              hardware structures set.
