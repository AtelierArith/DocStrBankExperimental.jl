```
with_buffer(f::Function, buf::ThreadsBuffer)
```

Execute function `f` with buffer `buf`.

The buffer is released after the function is executed.

# Example

```julia
julia> buf = Buffer(10000)
julia> C = alloc!(buf, 10, 10, 20) # 10x10x20 destination tensor on a single thread
julia> tbuf = ThreadsBuffer(1000)
julia> Threads.@threads for k = 1:20
          with_buffer(tbuf) do bu
            A = alloc!(bu, 10, 10) # 10x10 tensor
            B = alloc!(bu, 10, 10) # 10x10 tensor
            rand!(A)
            rand!(B)
            @tensor C[:,:,k][i,j] = A[i,l] * B[l,j]
          end
        end
```
