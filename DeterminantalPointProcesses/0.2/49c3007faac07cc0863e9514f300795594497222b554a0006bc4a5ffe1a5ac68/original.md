```
DeterminantalPointProcess(L::AbstractMatrix; parallelize=false)
DeterminantalPointProcess(L::Eigen; parallelize=false)
```

Given a symmetric matrix `L`, creates a `DeterminantalPointProcess` (DPP). One can also pass the eigen object directly

---

```
DeterminantalPointProcess(kernel::Kernel, X::AbstractVector; parallelize=false)
DeterminantalPointProcess(kernel::Kernel, X::AbstractMatrix; obsdim=1; parallelize=false)
```

Similar to the basic constructor, will first build the kernel matrix with `kernel` on observations `X`. If your input is a `AbstractMatrix` you can pass the `obsdim` argument to indicate if rows or columns represent the samples (see docs of [KernelFunctions](https://juliagaussianprocesses.github.io/KernelFunctions.jl/stable/))
