```
replacebond!(M::MPS, b::Int, phi::ITensor; kwargs...)
```

Factorize the ITensor `phi` and replace the ITensors `b` and `b+1` of MPS `M` with the factors. Choose the orthogonality with `ortho="left"/"right"`.
