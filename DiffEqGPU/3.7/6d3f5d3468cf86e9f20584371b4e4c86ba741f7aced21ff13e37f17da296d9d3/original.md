```julia
EnsembleCPUArray(cpu_offload = 0.2)
```

An `EnsembleArrayAlgorithm` which utilizes the CPU kernels to parallelize each ODE solve with their separate ODE integrator on each kernel. This method is meant to be a debugging counterpart to `EnsembleGPUArray`, having the same behavior and using the same KernelAbstractions.jl process to build the combined ODE, but without the restrictions of `f` being a GPU-compatible kernel function.

It is unlikely that this method is useful beyond library development and debugging, as almost any case should be faster with `EnsembleThreads` or `EnsembleDistributed`.
