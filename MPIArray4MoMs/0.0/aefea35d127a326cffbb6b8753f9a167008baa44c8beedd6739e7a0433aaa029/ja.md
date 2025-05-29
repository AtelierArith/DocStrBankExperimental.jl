```
slicedim2bounds(dims, nc::Int)
```

将区间 `dims` 划分为 `nc` 个区间并返回区间上下界。 *[MoM_Kernels](https://github.com/deltaeecs/MoM_Kernels.jl) はこの関数を借用します。これは、MPIを早期に導入することによるクラスタ上のバグを避けるためです。したがって、この関数の変更は [MoM_Kernels](https://github.com/deltaeecs/MoM_Kernels.jl) と同期する必要があります。*
