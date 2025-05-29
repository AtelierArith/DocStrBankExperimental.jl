```julia
struct LaplacianKernel <: CompressiveLearning.Kernel
```

k(x,y) = exp(-λ‖x-y‖₁) Implies p(ω)∝ Π Cauchy(0, λ)
