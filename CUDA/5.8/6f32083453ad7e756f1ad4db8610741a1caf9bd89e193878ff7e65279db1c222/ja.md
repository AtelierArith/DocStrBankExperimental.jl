```
cudacall(f, types, values...; blocks::CuDim, threads::CuDim,
         cooperative=false, shmem=0, stream=stream())
```

GPU上でCUDA関数`f`を起動するための`ccall`-のようなインターフェース。

例えば：

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

`blocks`および`threads`引数は起動構成を制御し、どちらも整数または1から3の整数のタプルで構成される必要があります（省略された次元はデフォルトで1になります）。`types`引数には、型のタプルとタプル型の両方を含めることができ、後者の方がわずかに高速です。
