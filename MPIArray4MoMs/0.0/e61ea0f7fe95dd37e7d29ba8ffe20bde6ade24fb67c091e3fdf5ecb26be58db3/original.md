```
sizeChunksCuts2indices(Asize, nchunk, cuts::Tuple)
sizeChunksCuts2indices(Asize, nchunk, cuts::Vector{I}) where{I<:Integer}
```

根据数组大小 `Asize` 分块数量 `nchunk` 以及各块索引区间 `cuts` 计算各块的索引。 *[MoM_Kernels](https://github.com/deltaeecs/MoM_Kernels.jl) 会借用此函数， 为的是避免提前引入 MPI 导致在集群上的 bug。因此该函数的修改必须与  [MoM_Kernels](https://github.com/deltaeecs/MoM_Kernels.jl) 同步。*
