```julia
copyat_or_push!{T}(a::AbstractVector{T}, i::Int, x)
```

If `i<length(x)`, it's simply a `recursivecopy!` to the `i`th element. Otherwise, it will `push!` a `deepcopy`.
