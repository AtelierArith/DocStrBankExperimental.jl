```julia
struct LaplacianKernel <: CompressiveLearning.Kernel
```

k(x,y) = exp(-λ‖x-y‖₁) は p(ω)∝ Π Cauchy(0, λ) を意味します。
