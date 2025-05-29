```
CUDALibs()
CUDALibs(settings)
```

Indicate that computation should be performing using the CUDA libraries. Optionally pass in an object specifying algorithmic settings.

# Examples:

```julia
filter(CUDALibs(), image, kernel)
filter(CUDALibs(backend), image, kernel)
```
