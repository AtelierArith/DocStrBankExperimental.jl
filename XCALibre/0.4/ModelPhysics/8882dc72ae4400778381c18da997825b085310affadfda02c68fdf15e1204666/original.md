```
turbulence!(rans::KOmegaModel, model::Physics{T,F,M,Tu,E,D,BI}, S, prev, time, config
) where {T,F,M,Tu<:AbstractTurbulenceModel,E,D,BI}
```

Run turbulence model transport equations.

### Input

  * `rans::KOmegaModel` – KOmega turbulence model.
  * `model`  – Physics model defined by user.
  * `S`   – Strain rate tensor.
  * `prev`  – Previous field.
  * `time`   –
  * `config` – Configuration structure defined by user with solvers, schemes, runtime and              hardware structures set.
