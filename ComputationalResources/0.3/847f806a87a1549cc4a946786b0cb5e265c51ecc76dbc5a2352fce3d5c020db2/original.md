```
OpenCLLibs()
OpenCLLibs(settings)
```

Indicate that computation should be performing using the OpenCL libraries. Optionally pass in an object specifying algorithmic settings.

# Examples:

```julia
filter(OpenCLLibs(), image, kernel)
filter(OpenCLLibs(backend), image, kernel)
```
