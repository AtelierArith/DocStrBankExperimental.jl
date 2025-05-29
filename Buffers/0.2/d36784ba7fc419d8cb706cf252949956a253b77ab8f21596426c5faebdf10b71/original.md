```
neuralyze(tensor::AbstractArray)
```

Wipe the memory about origin of `tensor`.

`tensor` is a (contiguous!) array that is a (possibly reshaped) view of a larger array.   Return the same tensor pointing to the same memory,    but without the information about the origin.   To be used together with [`alloc!`](@ref) or [`reshape_buf!`](@ref) to trick `Base.mightalias`.

!!! warning
    Note that this function is unsafe and should be used with caution! If too much memory is wiped, Julia might garbage-collect the original array and the tensor will point to invalid memory. Also don't use this function if the buffer-size might change in between.


!!! tip
    One can use `GC.@preserve` to prevent the garbage collection of the original array  (however, this shouldn't be necessary).


# Example

```julia
julia> buf = Buffer(100000)
julia> A = alloc(buf, 10, 10, 20) # 10x10x20 tensor
julia> B = alloc(buf, 10, 10, 10) # 10x10x10 tensor starting after A
julia> C = alloc(buf, 10, 20) # 10x20 tensor starting after B
julia> rand!(B)
julia> rand!(C)
julia> An = neuralyze(A) # tensor without origin but pointing to the same memory
julia> @tensor An[i,j,k] = B[i,j,l] * C[l,k]
```
