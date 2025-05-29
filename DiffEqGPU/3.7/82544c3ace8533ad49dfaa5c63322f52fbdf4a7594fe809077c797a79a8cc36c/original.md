```julia
EnsembleGPUKernel(backend, cpu_offload = 0.0)
```

A massively-parallel ensemble algorithm which generates a unique GPU kernel for the entire ODE which is then executed. This leads to a very low overhead GPU code generation, but imparts some extra limitations on the use.

## Positional Arguments

  * `backend`: the KernelAbstractions backend for performing the computation.
  * `cpu_offload`: the percentage of trajectories to offload to the CPU. Default is 0.0 or 0% of trajectories.

## Limitations

  * Not all standard Julia `f` functions are allowed. Only Julia `f` functions which are capable of being compiled into a GPU kernel are allowed. This notably means that certain features of Julia can cause issues inside a kernel, like:

      * Allocating memory (building arrays)
      * Linear algebra (anything that calls BLAS)
      * Broadcast
  * Only out-of-place `f` definitions are allowed. Coupled with the requirement of not allowing for memory allocations, this means that the ODE must be defined with `StaticArray` initial conditions.
  * Only specific ODE solvers are allowed. This includes:

      * GPUTsit5
      * GPUVern7
      * GPUVern9
  * To use multiple GPUs over clusters, one must manually set up one process per GPU. See the multi-GPU tutorial for more details.

## Example

```julia
using DiffEqGPU, CUDA, OrdinaryDiffEq, StaticArrays

function lorenz(u, p, t)
    σ = p[1]
    ρ = p[2]
    β = p[3]
    du1 = σ * (u[2] - u[1])
    du2 = u[1] * (ρ - u[3]) - u[2]
    du3 = u[1] * u[2] - β * u[3]
    return SVector{3}(du1, du2, du3)
end

u0 = @SVector [1.0f0; 0.0f0; 0.0f0]
tspan = (0.0f0, 10.0f0)
p = @SVector [10.0f0, 28.0f0, 8 / 3.0f0]
prob = ODEProblem{false}(lorenz, u0, tspan, p)
prob_func = (prob, i, repeat) -> remake(prob, p = (@SVector rand(Float32, 3)) .* p)
monteprob = EnsembleProblem(prob, prob_func = prob_func, safetycopy = false)

@time sol = solve(
    monteprob, GPUTsit5(), EnsembleGPUKernel(CUDA.CUDABackend()), trajectories = 10_000,
    adaptive = false, dt = 0.1f0)
```
