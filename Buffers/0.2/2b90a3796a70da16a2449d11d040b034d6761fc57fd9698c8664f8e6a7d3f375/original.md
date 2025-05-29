```
ThreadsMAllocBuffer{T}
```

[`MAllocBuffer`](@ref) object to store data of type `T` for each thread.

By default, the buffer is created for `nthreads()` threads, i.e., each thread has its own buffer [`MAllocBuffer`](@ref).

Create the buffer with `ThreadsMAllocBuffer{T}(len, nbuf=Threads.nthreads())` and use it with [`alloc!`](@ref), [`drop!`](@ref), [`reset!`](@ref), etc.

!!! warning
    Always [`reset!`](@ref) or [`Buffers.release!`](@ref) the buffer after use in each thread!


!!! warning
    The memory is allocated manually, therefore the buffer must be freed manually as well. The buffer is intended to be used with [`@threadsbuffer`](@ref) macro, which frees the buffer after use.


# Example

```julia
@buffer buf(10000) begin
  C = alloc!(buf, 10, 10, 20) # 10x10x20 destination tensor on a single thread
  @threadsbuffer tbuf(1000) begin # 1000 elements buffer for nthreads() threads each
    @sync for k = 1:20
      Threads.@spawn begin
        A = alloc!(tbuf, 10, 10) # 10x10 tensor
        B = alloc!(tbuf, 10, 10) # 10x10 tensor
        rand!(A)
        rand!(B)
        @tensor C[:,:,k][i,j] = A[i,l] * B[l,j]
        reset!(tbuf)
      end 
    end
  end # free threadsbuffer tbuf
end # free buffer buf
```
