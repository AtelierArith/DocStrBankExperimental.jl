```
ash!(o::Ash; kw...)
ash!(o::Ash, newdata; kw...)
ash!(o::Ash, newdata, weight::AbstractWeights; kw...)
```

Update an Ash estimate with new data, new weight, smoothing parameter (keyword `m`), or kernel (keyword `kernel`):
