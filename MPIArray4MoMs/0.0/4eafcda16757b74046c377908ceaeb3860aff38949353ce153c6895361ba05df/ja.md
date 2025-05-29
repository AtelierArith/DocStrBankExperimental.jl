```
sizeChunks2idxs(Asize, nchunk)
```

[DistributedArray.jl](https://github.com/JuliaParallel/DistributedArrays.jl) から借用したもので、各次元での `nchunk` に基づいて行列サイズ `Asize` のスライスを取得します。 *[MoM_Kernels](https://github.com/deltaeecs/MoM_Kernels.jl) はこの関数を借用しており、MPI を事前に導入することでクラスタ上のバグを回避するためです。したがって、この関数の変更は [MoM_Kernels](https://github.com/deltaeecs/MoM_Kernels.jl) と同期する必要があります。*
