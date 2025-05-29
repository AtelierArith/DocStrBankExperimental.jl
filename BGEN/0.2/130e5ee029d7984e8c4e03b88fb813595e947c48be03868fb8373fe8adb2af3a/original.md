```
hardcall(d::AbstractArray{T}; threshold=0.1) where {I, T}
```

Hard genotype calls for dosages. `d` is the dosage vector, the return UInt8 vector is filled with the hard called genotypes  with values 0, 1, 2, or 9 (for missing). `threshold` determines maximum distance between the hardcall and the dosage. `threshold` must be in [0, 0.5). 
