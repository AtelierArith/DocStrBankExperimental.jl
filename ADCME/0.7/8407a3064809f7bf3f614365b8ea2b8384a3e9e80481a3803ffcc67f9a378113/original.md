```
has_gpu()
```

Check if the TensorFlow backend is using CUDA GPUs. Operators that have GPU implementations will be executed on GPU devices.  See also [`get_gpu`](@ref)

!!! note
    ADCME will use GPU automatically if GPU is available. To disable GPU, set the environment variable `ENV["CUDA_VISIBLE_DEVICES"]=""` before importing ADCME

