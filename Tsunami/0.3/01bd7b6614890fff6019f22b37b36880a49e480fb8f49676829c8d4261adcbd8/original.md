```
Foil(; kws...)
```

A type that takes care of the acceleration of the training process.

# Constructor Arguments

  * **accelerator**: Supports passing different accelerator types:

      * `:auto` (default): Automatically select a gpu if available, otherwise fallback on cpu.
      * `:gpu`: Like `:auto`, but will throw an error if no gpu is available.  In order for a gpu to be available, the corresponding package must be loaded (e.g. with `using CUDA`).  The trigger packages are `CUDA.jl` for Nvidia GPUs, `AMDGPU.jl` for AMD GPUs, and `Metal.jl` for Apple Silicon.
      * `:cpu`: Force using the cpu.

    See also the `devices` option.
  * **devices**: Pass an integer `n` to train on `n` devices (only `1` supported at the moment),   or a list of devices ids to train on specific devices (e.g. `[2]` to train on gpu with idx 2).   Ids indexing starts from `1`. If `nothing`, will use the default device    (see `MLDataDevices.gpu_device` documentation).    Default: `nothing`.
  * **precision**: Supports passing different precision types `(:bf16, :f16, :f32, :f64)`,    where `:bf16` is BFloat16, `:f16` is Float16, `:f32` is Float32, and `:f64` is Float64.   Default: `:f32`.
