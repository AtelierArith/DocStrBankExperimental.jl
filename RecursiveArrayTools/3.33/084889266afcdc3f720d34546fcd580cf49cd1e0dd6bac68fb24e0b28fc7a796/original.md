```julia
recursivecopy(a::Union{AbstractArray{T, N}, AbstractVectorOfArray{T, N}})
```

A recursive `copy` function. Acts like a `deepcopy` on arrays of arrays, but like `copy` on arrays of scalars.
