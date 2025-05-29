```
access!(pool::CuMemoryPool, dev::CuDevice, flags::CUmemAccess_flags)
access!(pool::CuMemoryPool, devs::Vector{CuDevice}, flags::CUmemAccess_flags)
```

Control the visibility of memory pool `pool` on device `dev` or a list of devices `devs`.
