```
cascade_and_unite(models::AbstractVector{U}) where {T, U <: AdmittanceModel{T}}
cascade_and_unite(models::Vararg{U}) where {T, U <: AdmittanceModel{T}}
```

Cascade all models and unite ports with the same name.
