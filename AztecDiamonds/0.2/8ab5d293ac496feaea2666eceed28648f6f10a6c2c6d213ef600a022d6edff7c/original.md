```
ka_diamond(N::Int, ArrayT::Type{<:AbstractArray}) -> Tiling{ArrayT{Edge}}
```

Generate a uniformly random diamond tiling just like [`diamond`](@ref), but using `KernelAbstractions.jl` to be able to take advantage of (GPU) parallelism. `ArrayT` can either be `Array` or any GPU array type.

Ref [`Tiling`](@ref)
