```
basetype(T::Type)
```

Recursively apply `eltype` to `T` until convergence.

# Examples

```jldoctest; setup = :(using EltypeExtensions: basetype)
julia> basetype(Matrix{BitArray})
Bool

julia> basetype(Vector{Set{Complex{Float64}}})
ComplexF64 (alias for Complex{Float64})

julia> basetype([1:n for n in 1:10])
Int64
```
