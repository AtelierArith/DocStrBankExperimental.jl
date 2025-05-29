```
cascade(ams::AbstractVector{U}) where {T, U <: AdmittanceModel{T}}
cascade(ams::Vararg{U}) where {T, U <: AdmittanceModel{T}}
```

モデルを1つの大きなブロック対角モデルにカスケードします。
