```
tr(v::MultiValue{Tuple{D,D,D2}}) -> ::VectorValue{D2}
```

Return a vector of length `D2` of traces computed on the first two indices: `resⱼ = Σᵢ vᵢᵢⱼ`.
