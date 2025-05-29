```
cascade_and_unite(models::AbstractVector{U}) where {T, U <: AdmittanceModel{T}}
cascade_and_unite(models::Vararg{U}) where {T, U <: AdmittanceModel{T}}
```

すべてのモデルをカスケードし、同じ名前のポートを統合します。
