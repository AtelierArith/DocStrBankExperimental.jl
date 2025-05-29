```
reshape_buf!(buf, dims...; offset=0, extend=true)
```

Reshape (part of) a buffer to given dimensions (without copying),   using `offset`.

For `ThreadsBuffer`, reshape the buffer of the current thread.   Call [`reset!(::ThreadsBuffer)`](@ref) or [`release!`](@ref) after use.

It can be used, e.g., for itermediates in tensor contractions.

!!! warning
    Do not use this function together with [`alloc!`](@ref) or [`drop!`](@ref) on the same buffer!


# Example

```julia
julia> buf = Buffer(100000)
julia> A = reshape_buf!(buf, 10, 10, 20) # 10x10x20 tensor
julia> B = reshape_buf!(buf, 10, 10, 10, offset=2000) # 10x10x10 tensor starting at 2001
julia> B .= rand(10,10,10)
julia> C = rand(10,20)
julia> @tensor A[i,j,k] = B[i,j,l] * C[l,k]
```
