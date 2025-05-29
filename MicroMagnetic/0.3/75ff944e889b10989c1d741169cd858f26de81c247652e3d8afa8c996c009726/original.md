```
set_backend(backend="cuda")
```

Set the backend of MicroMagnetic. This function allows you to specify the backend for MicroMagnetic simulations. 

The available options and their corresponding hardware and backends are shown below:

| Option              | Hardware   | Backend                    |
|:------------------- |:---------- |:-------------------------- |
| "cpu"               | CPU        | `KernelAbstractions.CPU()` |
| "cuda" or "nvidia"  | NVIDIA GPU | `CUDA.CUDABackend()`       |
| "amd" or "roc"      | AMD GPU    | `AMDGPU.ROCBackend()`      |
| "oneAPI" or "intel" | Intel GPU  | `oneAPI.oneAPIBackend()`   |
| "metal" or "apple"  | Apple GPU  | `Metal.MetalBackend()`     |

# Examples

To set the backend to use CUDA (NVIDIA GPU):

```julia
using MicroMagnetic
using CUDA
```

To set the backend to use the CPU/CUDA:

```
set_backend("cpu")
set_backend("cuda")
```
