```
basetype(T::Type)
```

`eltype`を`T`に再帰的に適用し、収束するまで続けます。

# 例

```jldoctest; setup = :(using EltypeExtensions: basetype)
julia> basetype(Matrix{BitArray})
Bool

julia> basetype(Vector{Set{Complex{Float64}}})
ComplexF64 (alias for Complex{Float64})

julia> basetype([1:n for n in 1:10])
Int64
```
