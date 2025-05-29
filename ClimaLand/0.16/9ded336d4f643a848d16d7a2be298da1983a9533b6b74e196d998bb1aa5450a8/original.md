```
AbstractImExModel{FT} <: AbstractModel{FT}
```

An abstract type for models which must be treated implicitly (and which may also have tendency terms that can be treated explicitly). This inherits all the default function definitions from AbstractModel, as well as `make_imp_tendency` and `make_compute_imp_tendency` defaults.
