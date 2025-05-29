```
sizeChunksCuts2indices(Asize, nchunk, cuts::Tuple)
sizeChunksCuts2indices(Asize, nchunk, cuts::Vector{I}) where{I<:Integer}
```

配列のサイズ `Asize`、チャンク数 `nchunk`、および各チャンクのインデックス範囲 `cuts` に基づいて、各チャンクのインデックスを計算します。 *[MoM_Kernels](https://github.com/deltaeecs/MoM_Kernels.jl) はこの関数を利用して、MPIを事前に導入することによるクラスタ上のバグを回避します。したがって、この関数の変更は [MoM_Kernels](https://github.com/deltaeecs/MoM_Kernels.jl) と同期する必要があります。*
