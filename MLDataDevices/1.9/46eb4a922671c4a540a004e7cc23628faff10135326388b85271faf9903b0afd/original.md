```
gpu_device(device_id::Union{Nothing, Integer}=nothing;
    force::Bool=false) -> AbstractDevice
```

Selects GPU device based on the following criteria:

1. If `gpu_backend` preference is set and the backend is functional on the system, then that device is selected.
2. Otherwise, an automatic selection algorithm is used. We go over possible device backends in the order specified by `supported_gpu_backends()` and select the first functional backend.
3. If no GPU device is functional and  `force` is `false`, then `cpu_device()` is invoked.
4. If nothing works, an error is thrown.

## Arguments

  * `device_id::Union{Nothing, Integer}`: The device id to select. If `nothing`, then we return the last selected device or if none was selected then we run the autoselection and choose the current device using `CUDA.device()` or `AMDGPU.device()` or similar. If `Integer`, then we select the device with the given id. Note that this is `1`-indexed, in contrast to the `0`-indexed `CUDA.jl`. For example, `id = 4` corresponds to `CUDA.device!(3)`.

!!! warning
    `device_id` is only applicable for `CUDA` and `AMDGPU` backends. For `Metal`, `oneAPI` and `CPU` backends, `device_id` is ignored and a warning is printed.


!!! warning
    `gpu_device` won't select a CUDA device unless both CUDA.jl and cuDNN.jl are loaded. This is to ensure that deep learning operations work correctly. Nonetheless, if cuDNN is not loaded you can still manually create a `CUDADevice` object and use it (e.g. `dev = CUDADevice()`).


## Keyword Arguments

  * `force::Bool`: If `true`, then an error is thrown if no functional GPU device is found.
