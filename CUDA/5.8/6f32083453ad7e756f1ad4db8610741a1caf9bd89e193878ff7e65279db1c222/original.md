```
cudacall(f, types, values...; blocks::CuDim, threads::CuDim,
         cooperative=false, shmem=0, stream=stream())
```

`ccall`-like interface for launching a CUDA function `f` on a GPU.

For example:

```
vadd = CuFunction(md, "vadd")
a = rand(Float32, 10)
b = rand(Float32, 10)
ad = alloc(CUDA.DeviceMemory, 10*sizeof(Float32))
unsafe_copyto!(ad, convert(Ptr{Cvoid}, a), 10*sizeof(Float32)))
bd = alloc(CUDA.DeviceMemory, 10*sizeof(Float32))
unsafe_copyto!(bd, convert(Ptr{Cvoid}, b), 10*sizeof(Float32)))
c = zeros(Float32, 10)
cd = alloc(CUDA.DeviceMemory, 10*sizeof(Float32))

cudacall(vadd, (CuPtr{Cfloat},CuPtr{Cfloat},CuPtr{Cfloat}), ad, bd, cd; threads=10)
unsafe_copyto!(convert(Ptr{Cvoid}, c), cd, 10*sizeof(Float32)))
```

The `blocks` and `threads` arguments control the launch configuration, and should both consist of either an integer, or a tuple of 1 to 3 integers (omitted dimensions default to 1). The `types` argument can contain both a tuple of types, and a tuple type, the latter being slightly faster.
