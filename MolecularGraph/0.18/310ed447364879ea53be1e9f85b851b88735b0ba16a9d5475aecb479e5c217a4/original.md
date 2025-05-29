```
massspec_peaks(mol::MolGraph; threshold=0.001) -> Matrix{Float64}
```

Return a vector of tuples of each isotopic masses and their relative intensity in the simulated mass spectrum (base peak intensity = 100).

Records that have lower abundance (not peak intensity) than the given threshold will be filtered out (default 0.001 = 0.1%)
