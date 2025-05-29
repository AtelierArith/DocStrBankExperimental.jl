```
compatible(psos::AbstractVector{PSOModel{T, U}}) where {T, U}
compatible(bboxes::AbstractVector{Blackbox{T, U}}) where {T, U}
```

Check if the models can be cascaded. Always true for PSOModels and true for Blackboxes that share the same value of `ω`.
