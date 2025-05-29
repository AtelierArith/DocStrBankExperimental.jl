```
slicedim2bounds(dims, nc::Int)
```

将区间 `dims` 划分为 `nc` 个区间并返回区间上下界。 *[MoM_Kernels](https://github.com/deltaeecs/MoM_Kernels.jl) 会借用此函数， 为的是避免提前引入 MPI 导致在集群上的 bug。因此该函数的修改必须与  [MoM_Kernels](https://github.com/deltaeecs/MoM_Kernels.jl) 同步。*
