```
BetaRandomSampler(pde_points, bcs_points=pde_points; sampling_alg=SobolSample(),
                  resample::Bool=false, α=0.4, β=1.0)
```

`QuasiRandomSampler`と同様ですが、ドメイン上の時間に沿って`Beta`分布を使用します。
