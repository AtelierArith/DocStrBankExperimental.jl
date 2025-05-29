```
normalizek(krs::AbstractVector{<:KRatios}; norm::Float32=1.0f)::Vector{KRatios}
normalizek(krs::AbstractVector{KRatio}; norm::Float32=1.0f)::Vector{KRatio}
```

Computes the pixel-by-pixel normalized k-ratio for each point in the KRatios data array. `norm` specifies normalization constants other than 1.0.
