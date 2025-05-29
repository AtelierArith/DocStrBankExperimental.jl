```
Session(args...; kwargs...)
```

Create an ADCME session. By default, ADCME will take up all the GPU resources at the start. If you want the GPU usage to grow on a need basis, before starting ADCME, you need to set the environment variable via

```julia
ENV["TF_FORCE_GPU_ALLOW_GROWTH"] = "true"
```

# Configuration

Session accepts some runtime optimization configurations 

  * `intra`: Number of threads used within an individual op for parallelism
  * `inter`: Number of threads used for parallelism between independent operations.
  * `CPU`: Maximum number of CPUs to use.
  * `GPU`: Maximum number of GPU devices to use
  * `soft`: Set to True/enabled to facilitate operations to be placed on CPU instead of GPU

!!! note
    `CPU` limits the number of CPUs being used, not the number of cores or threads.

