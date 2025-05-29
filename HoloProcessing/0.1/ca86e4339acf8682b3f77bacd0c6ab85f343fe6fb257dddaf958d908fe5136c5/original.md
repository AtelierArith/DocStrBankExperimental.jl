```
normalize!(x::AbstractMatrix; nthreads=false) -> AbstractMatrix
```

对矩阵`x`进行`原地`归一化，即原地修改矩阵并返回修改后的`x`

# Arguments

  * `x`: 矩阵
  * `x`: 矩阵
  * `nthreads`: 决定是否开多线程来进行归一化，默认为否

# Notice

对于不大的矩阵（低于10*000 × 10*000），不建议开多线程，这是因为多线程会有额外的内存和时间开销
