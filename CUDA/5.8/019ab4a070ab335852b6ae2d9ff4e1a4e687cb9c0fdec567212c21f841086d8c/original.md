```
device_reset!(dev::CuDevice=device())
```

Reset the CUDA state associated with a device. This call with release the underlying context, at which point any objects allocated in that context will be invalidated.

Note that this does not guarantee to free up all memory allocations, as many are not bound to a context, so it is generally not useful to call this function to free up memory.

!!! warning
    This function is only reliable on CUDA driver >= v12.0, and may lead to crashes if used on older drivers.

