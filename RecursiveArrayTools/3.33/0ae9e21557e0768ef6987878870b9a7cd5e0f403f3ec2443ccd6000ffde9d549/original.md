```julia
recursivecopy!(b::AbstractArray{T, N}, a::AbstractArray{T, N})
```

A recursive `copy!` function. Acts like a `deepcopy!` on arrays of arrays, but like `copy!` on arrays of scalars.
