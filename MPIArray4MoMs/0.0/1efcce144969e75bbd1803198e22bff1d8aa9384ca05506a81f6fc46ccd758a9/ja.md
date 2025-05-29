```
sizeChunks2cuts(Asize, chunks)
sizeChunks2cuts(Asize::Int, chunks)
sizeChunks2cuts(Asize, chunks::Int)
sizeChunks2cuts(Asize::Int, chunks::Int)
```

配列のサイズ `Asize` を `chunks` に従って分割します。 *[MoM_Kernels](https://github.com/deltaeecs/MoM_Kernels.jl) はこの関数を借用し、MPIを事前に導入することによるクラスタ上のバグを回避するためです。したがって、この関数の変更は [MoM_Kernels](https://github.com/deltaeecs/MoM_Kernels.jl) と同期する必要があります。*
