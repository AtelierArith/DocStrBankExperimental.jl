```julia
struct GaussianKernel <: CompressiveLearning.Kernel
```

k(x,y) = exp(-‖x-y‖₂²/(2σ²)) は p(ω)∝N(0, 1/σ²I) を意味します。
