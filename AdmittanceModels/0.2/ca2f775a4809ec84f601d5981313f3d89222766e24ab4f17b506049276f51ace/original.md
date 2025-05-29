```
cascade(ams::AbstractVector{U}) where {T, U <: AdmittanceModel{T}}
cascade(ams::Vararg{U}) where {T, U <: AdmittanceModel{T}}
```

Cascade the models into one larger block diagonal model.
