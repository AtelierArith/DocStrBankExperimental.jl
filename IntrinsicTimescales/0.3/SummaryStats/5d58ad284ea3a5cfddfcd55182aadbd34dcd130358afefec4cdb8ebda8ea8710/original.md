```
bat_integrated_autocorr_weight(
    samples::DensitySampleVector;
    c::Integer = 5, tol::Integer = 50, strict = true
)
```

Estimate the integrated autocorrelation weight of `samples`.

Uses [`bat_integrated_autocorr_len`](@ref).     
