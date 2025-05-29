```
extract_coefs(models::Vector{<:UnfoldModel}, predictor, basisname)
```

When applied to a vector of Unfold models, extracts the coefficients (matching the predictor and basisname) for all models (usually subjects) and concatenates them.

The dimensions of the returned coefficients are channel x times x coefficients x subjects.
