```
BetaRandomSampler(pde_points, bcs_points=pde_points; sampling_alg=SobolSample(),
                  resample::Bool=false, α=0.4, β=1.0)
```

Same as `QuasiRandomSampler`, but use `Beta` distribution along time on the domain.
