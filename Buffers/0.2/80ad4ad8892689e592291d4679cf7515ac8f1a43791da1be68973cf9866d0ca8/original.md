```
alloc!(buf, dims...; extend=true)
```

Allocate tensor of given dimensions in buffer `buf`.

The tensor is allocated in the buffer starting at the current offset.   The offset is increased by the length of the tensor.   If `extend=true`, the buffer is extended if necessary.   For `ThreadsBuffer`, the tensor is allocated in the buffer of the current thread.

Return the allocated tensor.

```julia
julia> buf = Buffer(100000)
julia> A = alloc!(buf, 10, 10, 20) # 10x10x20 tensor
julia> B = alloc!(buf, 10, 10, 10) # 10x10x10 tensor starting after A
julia> C = alloc!(buf, 10, 20) # 10x20 tensor starting after B
julia> rand!(B)
julia> rand!(C)
julia> An = neuralyze(A) # tensor without origin
julia> @tensor An[i,j,k] = B[i,j,l] * C[l,k]
```
