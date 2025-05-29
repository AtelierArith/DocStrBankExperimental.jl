```
sizeChunks2idxs(Asize, nchunk)
```

Borrowed form [DistributedArray.jl](https://github.com/JuliaParallel/DistributedArrays.jl), get the slice of matrix size `Asize` on each dimension with `nchunk`. *[MoM_Kernels](https://github.com/deltaeecs/MoM_Kernels.jl) 会借用此函数， 为的是避免提前引入 MPI 导致在集群上的 bug。因此该函数的修改必须与  [MoM_Kernels](https://github.com/deltaeecs/MoM_Kernels.jl) 同步。*
